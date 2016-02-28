# NLTK REST Server

This is a simple implementation that allows the Python [Natural Language Toolkit (NLTK)](http://nltk.org/)
to be called as a REST service. The package can be installed via pip and/or via setuptools.

## Installation

### Simple with PIP

 1. Just run `pip install nltkrest`
 
Please note, that b/c of the [NLTK Contrib](http://github.com/manalishah/nltk_contrib) fork
that we depend on and overall the fork and its upstreams unavailability in PyPI, we have to
use dependency_links, which may not be supported in pip in the future. You may need to pass
the `--process-dependency-links` to pip in order to install the software.

### Setuptools and/or Distribute
 
 1. Just run `python setup.py install`

After installation you will have a command called `nltk-server`. By default it starts a REST server
on port `8881`. You can change the port by typing `--port or -p`. You can also turn on verbose 
mode by typing `-v`.

## Start the NLTK Server 

To begin, start the server, turn on verbose mode, and change the port to 8888.

`nltk-server -v --port 8888`

## Example cURL client command

Now from the client, execute the following command:

`curl -X POST -d "Hi, my name is Abraham Lincoln. I live in Los Angeles, California." http://localhost:8888/nltk`

You should see back:

```
{
    "names": [
        "Hi",
        "Abraham Lincoln",
        "Los Angeles",
        "California"
    ],
    "result": "success"
}
```

## Example cURL client command with Dates/Times

We have added support for dates/times using the [NLTK Contrib Timex](https://github.com/nltk/nltk_contrib/blob/master/nltk_contrib/timex.py)
module. You can test it out by adding some date/time information to your text.

`curl -X POST -d "Hi, my name is Abraham Lincoln. I live in Los Angeles, California. Let's hang out tomorrow, Friday, February 26, 2016." http://localhost:8881/nltk`

Which should return:

```
{
    "names": [
        "Hi",
        "Abraham Lincoln",
        "Los Angeles",
        "California",
        "tomorrow",
        "2016"
    ],
    "result": "success"
}
```

You can use `PUT` or `POST` to send a message to the server. Also if you just contact at the `/` default endpoint,
you will see an HTML page that prints the status of the service.

Questions, comments?
===================
Send them to [Manali Shah](manalids@usc.edu) or [Chris A. Mattmann](mailto:chris.a.mattmann@jpl.nasa.gov).

Contributors
============
* Manali Shah, USC
* Chris A. Mattmann, USC & JPL

License
=======
[Apache License, version 2](http://www.apache.org/licenses/LICENSE-2.0)
