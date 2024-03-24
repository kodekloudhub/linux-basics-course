# Troubleshoot the Development Environment

[Troubleshoot](https://kodekloud.com/topic/lab-troubleshoot-the-development-environment/) the Development Environment


1. Information only
1. Information only
1.  <details>
    <summary>Copy the file <code>caleston-code.tar.gz</code> from Bob's laptop to Bob's home directory on the webserver <code>devapp01</code></summary>

    ```bash
    scp caleston-code.tar.gz devapp01:~/
    ```

    </details>
1.  <details>
    <summary>On the <code>devapp01</code> webserver, unzip and extract the copied file in the directory <code>/opt/</code>.</summary>

    Note that the `/opt` directory is owned by root on `devapp01` so we'll need sudo

    ```bash
    ssh devapp01

    sudo tar -zxf caleston-code.tar.gz -C /opt
    ```

    Don't exit from the ssh session just yet. We need to remain on `devapp01`

    </details>
1.  <details>
    <summary>Delete the tar file from <code>devapp01</code> webserver.</summary>

    ```bash
    rm caleston-code.tar.gz
    ```

    </details>
1.  <details>
    <summary>Make sure that the directory is extracted in such a way that the path <code>/opt/caleston-code/mercuryProject/</code> exists on the <code>webserver</code>.</summary>

    Nothing to do here. If you got Q4 right, then this will work too - press OK.

    You can verify if you like:

    ```bash
    ls -l /opt/caleston-code/mercuryProject/
    ```

    </details>
1.  <details>
    <summary>For the client demo, Bob has installed a <code>postgres</code> database in <code>devdb01</code>.</br>SSH to the database <code>devdb01</code> and check the status of the <code>postgresql.service</code></br>What is the state of the DB?</summary>

    At this point you are still logged into `devapp01`, so first return to Bob's laptop

    ```bash
    exit
    ```

    Now go to the db node

    ```bash
    ssh devdb01

    systemctl status postgresql.service
    ```

    Note the status: `Active: inactive (dead) ...`

    Don't exit from the ssh session just yet. We need to remain on `devdb01`
    </details>
1.  <details>
    <summary>Add an entry <code>host all all 0.0.0.0/0</code> md5 to the end of the file <code>/etc/postgresql/10/main/pg_hba.conf</code> on the DB server.</br>This will allow the web application to connect to the DB.</summary>

    ```bash
    sudo vi /etc/postgresql/10/main/pg_hba.conf
    ```

    Make the change as directed, save and exit `vi`.

    </details>
1.  <details>
    <summary>Start the <code>postgres</code> DB on the <code>devdb01</code> server.</summary>

    ```bash
    sudo systemctl start postgresql.service
    ```

    </details>
1.  <details>
    <summary>What port is <code>postgres</code> running on? Check using the <code>netstat</code> command?</summary>

    ```bash
    sudo netstat -ptean
    ```

    There's 2 entries for postgres, one each for IPv4 and IPv6, but both are using the same port. Note this port down - you will need it later!

    </details>
1.  <details>
    <summary>Back on the <code>devapp01</code> webserver. Attempt to start the web application by:</br>Navigate to the directory <code>/opt/caleston-code/mercuryProject</code></br>Next, run the command <code>python3 manage.py runserver 0.0.0.0:8000</code></summary>

    At this point you are still logged into `devdb01`, so first return to Bob's laptop

    ```bash
    exit
    ```

    Now go to the app node

    ```bash
    ssh devapp01

    cd /opt/caleston-code/mercuryProject
    python3 manage.py runserver 0.0.0.0:8000
    ```

    Note it dumps a stack trace on the screen, i.e. it crashed! Thus the answer is `No`.

    Press `CRTL + C`

    </details>
1.  <details>
    <summary>Why did the command not work?</summary>

    The answer to this is in the stack trace at the end. The app cannot connect to the database on the address and port indicated. Also remember the earlier question where you were asked to find the port that the database server is listening on!

    </details>
1.  <details>
    <summary>It appears that Bob did not configure his app to connect a <code>postgres</code> database running on a different server.</summary>

    That explains why things are working on his laptop and not in the `DEV` servers.

    It also appears that he is using the `wrong` port for postgres!

    1. Find the file in the directory under `/opt/caleston-code` that has a string matching DATABASES = {.
    1. Replace the value of `localhost` to `devdb01`
    1. In the same file fix the postgres port to match the port being used on `devdb01`

    For this, we need to first find the file we need to edit, so we're going to use `find` to find _files_ and use `grep` to find the specific text, with the `-l` switch to print the file path the text was found in.

    ```bash
    find . -type f -exec grep -l 'DATABASES = {' "{}" \;
    ```

    Edit the file that was returned by the above

    ```bash
    vi ./mercury/settings.py
    ```

    Scroll down to `DATABASES = {` and beneath this set the correct host and port. Save and exit.

    </details>
1.  <details>
    <summary>Now that has been set up, change the ownership of ALL files and directories under <code>/opt/caleston-code</code> to user <code>mercury</code>.</summary>

    You'll need to be root to reassign ownership

    ```bash
    sudo chown -R mercury /opt/caleston-code
    ```

    Note that sometimes this step is marked incorrect even though it *is* correct! Ignore this and move on. It has been reported to the lab team.

    </details>
1.  <details>
    <summary>Great! Everything should now be in order to restart the application.</summary>

    On the devapp01 server start the webserver again by running the command:

    1. Navigate to the directory `/opt/caleston-code/mercuryProject`
    1. Next, run the command `python3 manage.py runserver 0.0.0.0:8000`

    Note:- Make sure to activate the virtual environment using `source ../venv/bin/activate` within the current project before executing `python3 manage.py migrate`.

    If you've followed all the above steps, you should still be in directory `/opt/caleston-code/mercuryProject`

    Run the migration.

    ```bash
    source ../venv/bin/activate
    python3 manage.py migrate
    ```

    Start the app again so the question will validate.

    ```
    python3 manage.py runserver 0.0.0.0:8000
    ```

    **What is this venv stuff?**

    If you're considering learning Python (highly recommended as it is required in many DevOps jobs), this means Virtual ENVironment. It allows you to install Python packages on a project-by-project basis, thus not polluting the main Python installation. This is especially useful on your development environment where you may have multiple Python projects all with different package requirements.

    </details>
1.  <details>
    <summary>Well done! Now, for the final task before the client presentation.</summary>

    Create a new service called mercury.service with the following requirements.

    1. Service name: - `mercury.service`, WorkingDirectory: - `/opt/caleston-code/mercuryProject/`, Command to run: `/usr/bin/python3 manage.py runserver 0.0.0.0:8000`.
    1. Restart `on failure` and enable for `multi-user.target`.
    1. Run as user `mercury`.
    1. Set description: `Project Mercury Web Application`.

    Here we have to create a [systemd unit file](https://kodekloud.com/topic/creating-a-systemd-service/) to make the Python app be runnable as a service.

    First quit the running webapp by pressing `CTRL-C`

    Now create the unit file

    ```bash
    sudo vi /etc/systemd/system/mercury.service
    ```

    And put the following in to satisfy the question requirements

    ```
    [Unit]
    Description=Project Mercury Web Application

    [Service]
    ExecStart=/usr/bin/python3 manage.py runserver 0.0.0.0:8000
    Restart=on-failure
    WorkingDirectory=/opt/caleston-code/mercuryProject/
    User=mercury

    [Install]
    WantedBy=multi-user.target
    ```

    Now enable and start the service. We must run a `daemon-reload` whenever we have created, edited or deleted a unit file. Note that the `.service` extension is optional with `systemctl` commands. We can say `mercury.service`, or simply `mercury`

    ```bash
    sudo systemctl daemon-reload
    sudo systemctl enable mercury
    sudo systemctl start mercury
    ```

    </details>
1.  Information only - browse the running application!
