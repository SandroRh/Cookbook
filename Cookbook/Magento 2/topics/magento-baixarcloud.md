```
Usage:
 magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...

Arguments:
  files                              Files to copy. Use the remote: prefix to define remote locations.

Options:
  -r, --recursive                    Recursively copy entire directories
  -p, --project=PROJECT              The project ID or URL
      --host=HOST                    The project's API hostname
  -e, --environment=ENVIRONMENT      The environment ID
  -A, --app=APP                      The remote application name
      --worker=WORKER                A worker name
  -i, --identity-file=IDENTITY-FILE  An SSH identity (private key) to use
  -h, --help                         Display this help message
  -q, --quiet                        Do not output any message
  -V, --version                      Display this application version
  -y, --yes                          Answer "yes" to any yes/no questions; disable interaction
  -n, --no                           Answer "no" to any yes/no questions; disable interaction
  -v|vv|vvv, --verbose               Increase the verbosity of messages

Examples:
 Copy local files a.txt and b.txt to remote mount var/files:
   magento-cloud scp a.txt b.txt remote:var/files

 Copy remote files c.txt to current directory:
   magento-cloud scp remote:c.txt .

 Copy subdirectory dump/ to remote mount var/files:
   magento-cloud scp -r dump remote:var/logs

 Copy files inside subdirectory dump/ to remote mount var/files:
   magento-cloud scp -r dump/* remote:var/logs
```