# [octodns-playground](https://github.com/murshidazher/octodns-playground)

> A playground to test DNS as a Code using OctoDNS

- Official documentation - [OctoDNS Docs](https://octodns.readthedocs.io/en/latest/)
- [Supported Providers List](https://octodns.readthedocs.io/en/latest/index.html#providers) 
- Step by step instruction for [Digitalocean Setup](https://www.digitalocean.com/community/tutorials/how-to-deploy-and-manage-your-dns-using-octodns-on-ubuntu-18-04)

## Local Development

Activate the environment 

```sh
$ virtualenv env 
$ source env/bin/activate
```

Install the dependencies

```sh
$ pip install -r requirements.txt
$ octodns-sync --version
```

Load environment variables. Validate and run

```sh
$ export DIGITALOCEAN_OAUTH_TOKEN="your-token-here"

# validate
$ octodns-validate --config=./config/config.yaml

# plan
$ octodns-sync --config=./config/config.yaml

# apply
$ octodns-sync --config=./config/config.yaml --doit

# check
dig +short your-domain
```

## Additional Commands

```sh
# Compare DNS records between providers
# Shows differences between your config (source) and DigitalOcean (target)
$ octodns-compare --config=./config/config.yaml --a config --b digitalocean --zone fiat0x.com.

# Dump DNS records from DigitalOcean to fiat0x.com.yaml
$ octodns-dump --config=./config/config.yaml --output-dir ./config fiat0x.com. digitalocean
```
