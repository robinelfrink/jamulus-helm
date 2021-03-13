# Jamulus Helm Chart

[Jamulus](https://jamulus.io) is open source (GPL) networked music
performance software that enables live rehearsing, jamming and
performing with musicians located anywhere on the internet.

This chart will install Jamulus in headless server mode.

## Installing the chart

To install the chart with the release name jamulus:

```
$ helm install jamulus charts/jamulus/
```

The command deploys Jamulus on the Kubernetes cluster in the default
configuration. The configuration section lists the parameters that can
be configured during installation.

## Configuration

The following table lists the configurable parameters of the Jamulus
chart and their default values.

Parameter | Description | Default
--------- | ----------- | -------
`image.repository` | Jamulus container image repository | `grundic/jamulus`
`image.tag` | Jamulus container image tag | `3.5.7`
`image.pullPolicy` | Jamulus container image pull policy | `IfNotPresent`
`imagePullSecrets` | Image pull secrets | `[]`
`nameOverride` |  Override the app name | none
`fullnameOverride` | Override the app full name | none
`jamulus.centralServer` | Address of the central server | none
`jamulus.serverInfo` | Infos of this server | none
`jamulus.welcomeMessage` | Welcome message on connect | none
`serviceAccount.create` | Create ServiceAccount | `true`
`serviceAccount.annotations` | Annotations for service account. | `{}`
`serviceAccount.name` | ServiceAccount name | Auto generated
`podAnnotations` | Additional Pod annotatations | `{}`
`podSecurityContext` | Security context policies to add to the Pod | `{}`
`service.type` | The Service type | `ClusterIP`
`service.port` | The UDP Service port | `22124`
`service.nodePort` | The UDP nodePort if type is `NodePort` | `32124`
`resources` | Pod resource requests & limits | `{}`
`nodeSelector` | Node labels for Pod assignment | `{}`
`tolerations` |  Toleration labels for Pod assignment| `[]`

Specify each parameter using the `--set key=value[,key=value]` argument
to helm install. For example:

```
$ helm install jamulus charts/jamulus/ \
    --set jamulus.welcomeMessage="Welcome to my Jamulus"
```

Alternatively, a YAML file that specifies the values for the above
parameters can be provided while installing the chart. For example,

```
$ helm install jamulus charts/jamulus/ --values values.yaml
```
