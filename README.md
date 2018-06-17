# UsefulCommands
Commands that I find useful

----
## Crontab
Runs a pythonscript every minut and logs error to pv.txt

` * * * * * PYTHONPATH=/home/sebstr/.local/lib/python2.7/site-packages/ python /home/sebstr/master/cronjob.py -V > /home/sebstr/pv.txt 2>&1 `


----

## Hyper-V

**enable hyper-v** `bcdedit /set hypervisorlaunchtype auto`

----

## Cryptography

-- in CMDER

**To get sha256 checksum** `sha256sum filename`

**Load file with gpg** also see `gpg --help`
`gpg --import filename` and then `gpg --fingerprint`
