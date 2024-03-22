# notes
Programming and infra related notes

## Local Setup

To preview the site locally:

with python installed:
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
make run
```

run as docker container:
```bash
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material\
```