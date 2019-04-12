# Kong in Docker Compose

This is an altered version based on official teample [Kong][kong-site-url].
Because official alpine image not support start in container port "80"

### My Problem

The Problem I was facing, is upstream have 302 redirect. I have two machines, one is kong, another is app.
App is avaiable on address app.com, kong is available on address https://ikong.com in docker port 80:8000. kong set upstream to http://app.com:2003,
and make it avaiable on route  http:g.ikong.com, when app.com return a redirect (302 response) to app.com/web/index , outer page will redirect to g.ikong.com:8000/web/index,
which is not correct. To solve this problem, is launch kong in docker port 80:80. but offical container not allowed to.

### related links
- Solution from  [link](https://github.com/Kong/kong/issues/4173)
- nginx bind to port 80 disscuss [link](https://github.com/bitnami/bitnami-docker-nginx/issues/96)
- about set kong proxy to port 80 [link](https://github.com/Kong/docker-kong/issues/94)

# What is Kong?

You can find the official Docker distribution for Kong at [https://store.docker.com/images/kong](https://store.docker.com/images/kong).

# How to use this template

This Docker Compose template provisions a Kong container with a Postgres database, plus a nginx load-balancer. After running the template, the `nginx-lb` load-balancer will be the entrypoint to Kong.

To run this template execute:

```shell
$ docker-compose up
```

To scale Kong (ie, to three instances) execute:

```shell
$ docker-compose scale kong=3
```

Kong will be available through the `nginx-lb` instance on port `8000`, and `8001`. You can customize the template with your own environment variables or datastore configuration.

Kong's documentation can be found at [https://docs.konghq.com/][kong-docs-url].

## Issues

If you have any problems with or questions about this image, please contact us through a [GitHub issue][github-new-issue].

## Contributing

You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a [GitHub issue][github-new-issue], especially for more ambitious contributions. This gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you find out if someone else is working on the same thing.

[kong-site-url]: https://konghq.com/
[kong-docs-url]: https://docs.konghq.com/
[github-new-issue]: https://github.com/Kong/docker-kong/issues/new
