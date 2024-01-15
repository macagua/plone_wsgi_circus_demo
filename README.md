# Plone WSGI Circus Demo

A demonstration of Plone deployment with WSGI using Circus, A Process & Socket Manager.

This is pretty minimal, it's a bit stupid to not have
``zeoclient`` and ``zeoserver`` here, because you can't just
add a worker in [circus](https://circus.readthedocs.io/) the way it is running now.

While it works, it is just a proof of concept, and
I only added a Plone site as a test.

To start circus, run

```bash
./bin/circusd circus.ini
```

This keeps circus in the foreground.

You can experiment with ``circusctl`` which is similar to
``supervisorctl``.
Additionally, there is circus-top to experiment with,
and the awesome web interface that listens on
http://localhost:8080

Have fun

## Installation


Create a virtual environment, executing the following command:

```bash
$ python3.11 -m venv ./venv
```

Activate the virtual environment, executing the following command:

```bash
$ source ./venv/bin/activate
```

Install the pre-requirements Python dependencies, executing the following command:

```bash
$ ./venv/bin/pip install -r https://dist.plone.org/release/6.0-latest/requirements.txt
```

```bash
$ ./venv/bin/buildout -vvv
```

Run it using ``circusd``, executing the following command:

```bash
$ ./venv/bin/circusd ./circus.ini
```

Now visit [http://127.0.0.1:9999](http://127.0.0.1:9999), you should  see the **hello world** app. The difference now is that the socket is managed by Circus and there are several web workers that are accepting connections against it.

Also can run as a daemon service, executing the following command:

```bash
$ ./venv/bin/circusd --daemon ./circus.ini
```

You can checkout the monitor stats console, like a ``top`` command, executing the following command:

```bash
$ ./venv/bin/circus-top
```

You can checkout the status service, executing the following command:

```bash
$ ./venv/bin/circusctl status
```

You can start the circus service, executing the following command:

```bash
$ ./venv/bin/circusctl start
```

You can stop the circus service, executing the following command:

```bash
$ ./venv/bin/circusctl stop
```

You can restart the circus service, executing the following command:

```bash
$ ./venv/bin/circusctl restart
```

Full Documentation is available at [https://circus.readthedocs.io/](https://circus.readthedocs.io/).
