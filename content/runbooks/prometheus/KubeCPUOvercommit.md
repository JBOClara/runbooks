# KubeCPUOvercommit

## Meaning

The `KubeCPUOvercommit` indicate that the cluster cannot tolerate node failure.
For single-node evaluation clusters, this is known, and these alerts may be silenced.
For multi-node HA-ready production setups, these alerts fire when too many nodes become unhealthy to support high availability,
and they indicate that the nodes should be brought back to health or replaced.


## Impact

This is a critical alert. Whether a node goes down, it might cause an incident.

## Diagnosis

Check the list of pods without limits:

```console
kubectl get po -A -o custom-columns="Name:metadata.name,CPU-limit:spec.containers[*].resources.limits.cpu" | grep none
```

## Mitigation

TODO
