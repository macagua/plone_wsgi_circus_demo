# Plone WSGI Circus Demo

A demonstration of Plone deployment with WSGI using ``Circus``.

> [Circus](https://circus.readthedocs.io/), A Process & Socket Manager.

You can experiment with ``circusctl`` which is similar to
``supervisorctl``.
Additionally, there is ``circus-top`` to experiment with.

Have fun

---

## Installation

Here, a tutorial step by step of deployment with Plone WSGI using Circus:

### Pre dependencies

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

There are two demonstrations available based on possible base configurations of Zope with WSGI using the Circus tool:

### Zope standalone

For install a Zope standalone server, executing the following command:

```bash
$ ./venv/bin/buildout
```

This command above generates the WSGI ``zope-deploy.ini`` file used for the ``circusd`` command to start the service.

```bash
$ ./bin/circusd ./zope-deploy.ini
```

Now visit [http://localhost:8080/](http://localhost:8080/), you should can create and see the **Plone** website.

### Zeo Server and clients

For install a Zeo Server and clients, executing the following command:

```bash
$ ./venv/bin/buildout -c zeo.cfg
```

This command above generates the WSGI ``zeo-deploy.ini`` file used for the ``circusd`` command to start the service.

```bash
$ ./bin/circusd ./zeo-deploy.ini
```

Now visit the following links:

- [http://localhost:8082/](http://localhost:8082/), you should can create and see the **Plone** website running on Zeo client 1.

- [http://localhost:8083/](http://localhost:8083/), you should can create and see the **Plone** website running on Zeo client 2.

- [http://localhost:8084/](http://localhost:8084/), you should can create and see the **Plone** website running on Zeo client on debug mode.


---

## Circus scripts

Circus installs some scripts to manage this project.

### circus daemon

Run it using ``circusd``, executing the following command:

```bash
$ ./bin/circusd ./WSGI_NAME.ini
```

> Where ``WSGI_NAME`` you will be replace for the WSGI filename generated with the ``buildout`` command.

Also can run as a daemon service, executing the following command:

```bash
$ ./bin/circusd --daemon ./WSGI_NAME.ini
```

> Where ``WSGI_NAME`` you will be replace for the WSGI filename generated with the ``buildout`` command.

This keeps ``circusd`` in the foreground mode.

### circus top

You can checkout the monitor stats console, like a ``top`` command, executing the following command:

```bash
$ ./bin/circus-top
```

### circus control

You can checkout the status service, executing the following command:

```bash
$ ./bin/circusctl status
```

You can start the circus service, executing the following command:

```bash
$ ./bin/circusctl start
```

You can stop the circus service, executing the following command:

```bash
$ ./bin/circusctl stop
```

You can restart the circus service, executing the following command:

```bash
$ ./bin/circusctl restart
```

Full Documentation is available at [https://circus.readthedocs.io/](https://circus.readthedocs.io/).
