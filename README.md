## What is Apache APISIX API Gateway

Apache APISIX is a dynamic, real-time, high-performance API Gateway.

APISIX API Gateway provides rich traffic management features such as load balancing, dynamic upstream, canary release, circuit breaking, authentication, observability, and more.

You can use APISIX API Gateway to handle traditional north-south traffic, as well as east-west traffic between services.
At present, APISIX has been used in various industries, including NASA, Tencent Cloud, EU Digital Factory, Airbus, Airwallex, iQIYI, etc.

## How to run Apache APISIX

Apache APISIX supports stand-alone mode and also supports the use of etcd database as the configuration center.

### How to run APISIX using etcd as configuration center

```shell
docker-compose -p apisix up -d
```

#### Test example

Check that APISIX is running properly by running the following command on the host.

```
curl "http://127.0.0.1:9180/apisix/admin/services/" -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1'
```

The response indicates that apisix is running successfully:

```json
{
  "total": 0,
  "list": []
}
```

If you want to modify the default configuration of APISIX, you can use the following command to enter the APISIX container and modify the configuration file `./conf/config.yaml`, which will take effect after reloading APISIX. For details, please refer to `./conf/config-default.yaml`.

```
docker exec -it apache-apisix bash
```

For more information, you can refer to the [APISIX Website](https://apisix.apache.org/) and [APISIX Documentation](https://apisix.apache.org/docs/apisix/getting-started). If you encounter problems during use, you can ask for help through [slack and the mailing list](https://apisix.apache.org/docs/general/join/).

## Reload APISIX in a running container

If you change your custom configuration, you can reload APISIX (without downtime) by issuing.

```
docker exec -it apache-apisix apisix reload
```
This will run the `apisix reload` command in your container.

## Kubernetes Ingress

During the deployment process, in addition to the above operations, APISIX also derived the [`apisix-ingress-controller`](https://github.com/apache/apisix-ingress-controller), which can be deployed and used in the K8s environment more conveniently.

## License

Licensed under the Apache License, Version 2.0: [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)
