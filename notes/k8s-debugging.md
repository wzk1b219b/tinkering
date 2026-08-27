# Kubernetes Debugging Notes

Collected during the 2026-08-27 on-call shift.

## Pod stuck in Pending

- `kubectl describe pod <name>` and check Events.
- Common causes:
  - CPU/memory requests exceed allocatable node resources
  - PersistentVolume node affinity mismatch
  - NodeSelector or tolerations don't match any node

## CrashLoopBackOff

- `kubectl logs <pod> --previous` for the last attempt.
- Check liveness probe timeouts before assuming app bug.

## Cluster Autoscaler

- If nodes are needed but not scaling, check `cluster-autoscaler-status` ConfigMap.
- Look for `ScaleUpNotTried` or `MaxNodesReached` messages.

## Handy one-liner

```
kubectl get events --sort-by=.lastTimestamp -A | tail -50
```