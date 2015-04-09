[![Documentation Status](https://readthedocs.org/projects/eveonline-third-party-documentation/badge/?version=latest)](https://readthedocs.org/projects/eveonline-third-party-documentation/?badge=latest)

# eveonline-third-party-documentation
Documentation for EVE Online third-party developers. This covers things like the XML API, CREST, the Static Data Export (SDE), and SSO. You can read the latest version of the documentation [here](http://eveonline-third-party-documentation.readthedocs.org/en/latest/).

# Developing
## Setup
You will need to have python, pip and virtualenv installed (install virtualenv using pip) then run the following commands from inside the repo directory:

### Windows
    virtualenv venv
    venv\Scripts\activate
    pip install -r requirements.txt

### Linux/mac
    virtualenv venv
    source venv/bin/activate
    pip install -r requirements.txt

## Running
    mkdocs serve
