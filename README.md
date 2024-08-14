# Kubernetes
- 実務で使えそうなことをまとめていく

## port-forward
-  特定のpodにポートフォワーディングすることができる
`localhost:8888`宛の通信を`sample-pod`の`80/TCP`ポートに転送する
```shell
kubectl port-forward sample-pod 8888:80
```
- check (ExpectedHTTP 200 OK)
```shell
curl -I localhost:8888 
```

> [!TIP]
> `kubectl port-forward`の実行中に通信できるPodは同一の一つのPodのみ
> 例えば`multi-resource`ではdeploymentとserviceは別々でフォワーディングする

## Use Command in container

```shell
kubectl exec -it sample-pod -- /bin/bash
# or
kubectl exec -it sample-pod -- SOMECOMMAND
```