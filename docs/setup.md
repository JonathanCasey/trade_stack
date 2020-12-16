# Setup

# Using

### Database: PostgreSQL
If using PostgreSQL as a database for some or all data, the
[Getting Started docs on PostgreSQL](https://www.postgresqltutorial.com/postgresql-getting-started/)
are fantastic.



# Contributing

## One-time Setup

### Python environment in VSC
To support pytest, add the following to `.vscode/settings.json` in the root of
the repo:
```json
{
    "python.envFile": "${workspaceFolder}/.env",
    "python.testing.pytestArgs": [
        "."
    ],
    "python.testing.pytestEnabled": true,
    "terminal.integrated.env.windows": {
        "PYTHONPATH": "${workspaceFolder}/grand_trade_auto;${env:PYTHONPATH}",
    }
}
```

Also create a `.env` file in the root of the repo with the following line:
```
PYTHONPATH=C:\path\to\the\repo\root;${PYTHONPATH}
```

Note that in the above, if not on Windows, the semicolon `;` separator should be
replaced with a colon `:`.

This only works when opening the folder.  If opened as part of a multi-folder
project, the `"terminal.integrated.env.windows"` will not be applied.  While not
the most elegant, running
`$env:PYTHONPATH = 'C:\path\to\repo\grand_trade_auto;' + $env:PYTHONPATH` will
do the trick (the last part for the plus `+` sign and onwards can be omitted if
it is not set at all yet).


### CircleCI
If forking this project, CircleCI will need contexts setup.  See
`.circleci/config.yml` for the contexts needed; the contents should be mostly
obvious (e.g. `docker-hub-creds` is intended to defind the user/pass env vars).
For the Docker Hub password, an access token should be created on the Security
page of your Docker Hub account profile.