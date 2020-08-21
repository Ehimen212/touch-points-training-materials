# Training Topic

## Kubernets Basics

1.  What is Kubernetes?

2.  Components of Kubernetes<sup>1</sup>.

    ![image of components](images/components-of-kubernetes.png)<sup>3</sup>

3.  Controllers<sup>2</sup>:

    - What are they?
    - Types:
      - Deployments<sup>\*</sup>
      - Statefulsets<sup>\*</sup>
      - DaemonSets<sup>\*</sup>
      - Replicasets
      - Jobs
      - Garbage Collection
      - TTL Controller or Finished Resources
      - CronJob
      - ReplicationController

4.  Services and Ingress

    - Ingress:

      ```
        internet
           |
        [ Ingress ]
        --|-----|--
        [ Services ]
      ```

      - Types of Ingresses<sup>4</sup>:

        - Single Service Ingress:


            ```
            apiVersion: networking.k8s.io/v1beta1
            kind: Ingress
            metadata:
            name: test-ingress
            spec:
            backend:
               serviceName: testsvc
               servicePort: 80
            ```

         - Simple fanout:

          ```
            foo.bar.com -> 178.91.123.132 -> / foo    service1:4200
                                             / bar    service2:8080
          ```

          ```
            apiVersion: networking.k8s.io/v1beta1
            kind: Ingress
            metadata:
            name: simple-fanout-example
            annotations:
               nginx.ingress.kubernetes.io/rewrite-target: /
            spec:
            rules:
            - host: foo.bar.com
               http:
                  paths:
                  - path: /foo
                  backend:
                     serviceName: service1
                     servicePort: 4200
                  - path: /bar
                  backend:
                     serviceName: service2
                     servicePort: 8080

          ```

          - Name based virtual hosting


          ```
              foo.bar.com --|                 |-> foo.bar.com service1:80
                            | 178.91.123.132  |
              bar.foo.com --|                 |-> bar.foo.com service2:80

          ```

          ```
         apiVersion: networking.k8s.io/v1beta1
         kind: Ingress
         metadata:
         name: name-virtual-host-ingress
         spec:
         rules:
         - host: foo.bar.com
            http:
               paths:
               - backend:
                  serviceName: service1
                  servicePort: 80
         - host: bar.foo.com
            http:
               paths:
               - backend:
                  serviceName: service2
                  servicePort: 80

          ```

          - TLS


          ```
            apiVersion: v1
            kind: Secret
            metadata:
               name: testsecret-tls
               namespace: default
            data:
               tls.crt: base64 encoded cert
               tls.key: base64 encoded key
            type: kubernetes.io/tls


            apiVersion: networking.k8s.io/v1beta1
            kind: Ingress
            metadata:
            name: tls-example-ingress
            spec:
            tls:
            - hosts:
                  - sslexample.foo.com
               secretName: testsecret-tls
            rules:
            - host: sslexample.foo.com
               http:
                  paths:
                  - path: /
                  backend:
                     serviceName: service1
                     servicePort: 80

          ```

1: [components of kubernetes](https://kubernetes.io/docs/concepts/overview/components/)

2: [controllers](https://kubernetes.io/docs/concepts/workloads/controllers/)

3: [image source](https://kubernetes.io/docs/concepts/overview/components/)

4: [ingress explained](https://kubernetes.io/docs/concepts/services-networking/ingress/)
