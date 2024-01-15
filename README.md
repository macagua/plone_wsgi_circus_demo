# Plone WSGI Circus Demo

A demonstration of Plone deployment with WSGI using [Circus](https://circus.readthedocs.io/), A Process & Socket Manager.

You can experiment with ``circusctl`` which is similar to
``supervisorctl``.
Additionally, there is ``circus-top`` to experiment with.

Have fun

---

## Installation

Create a virtual environment, executing the following command:

```bash
$ python3 -m venv ./venv
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
$ ./venv/bin/circusd ./zope-deploy.ini
```

Now visit [http://localhost:8080/](http://localhost:8080/), you should see the **Plone** website.

Also can run as a daemon service, executing the following command:

```bash
$ ./venv/bin/circusd --daemon ./zope-deploy.ini
```

This keeps ``circusd`` in the foreground mode.

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
