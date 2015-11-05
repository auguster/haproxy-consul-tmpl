# haproxy-consul-tmpl
Improved template file for [haproxy-consul](https://github.com/CiscoCloud/haproxy-consul)
This allows to get rid of HAPROXY_DOMAIN variable completely.

# usage
The domain have to be stored in the tags of the services under the form `<domain>_<tld>`. If no tag is found for a service, it would be serve on every domain.

# example
For example, for a docker run command it would be:

`docker run --name blog -p 80 -v /data/blog/www:/var/www -e SERVICE_NAME=www -e SERVICE_TAGS=remisoft_info www`

in this example the service `www` would be served on the domain `remisoft.info`. The underscore are used because consul tags cannot contain dots. If the same service is to be served on multiple domain, just separate them by a comma. For example: `-e SERVICE_TAGS=remisoft_info,example_com`.
