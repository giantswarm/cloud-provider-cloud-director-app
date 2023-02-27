# cloud-provider-cloud-director-app

## How to install

### Modify values.yaml files

Below is the top level chart that spans both the CSI (cloud-director-named-disk-csi-driver) and the CPI (cloud-provider-for-cloud-director) in sub-charts. Note that upstream, the CSI and CPI are 2 distinct repositories that we merged together here as they will most likely be used together at all times.

`vi /helm/cloud-provider-cloud-director-app/values.yaml`

### Install with Helm

```
export KUBECONFIG=./<cluster>.kubeconfig 

helm install vcd-csi-cpi -n kube-system ./helm/cloud-provider-cloud-director-app/
```

### How to use the CSI

Create a storage class with the provisioner and storageProfile fields like so if it wasn't created by the chart:

``` yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  annotations:
    storageclass.kubernetes.io/is-default-class: "false"
  name: test-sc-xav
provisioner: named-disk.csi.cloud-director.vmware.com
reclaimPolicy: Delete
parameters:
  storageProfile: "vSAN-RAID-5"
  filesystem: "ext4"
```

The storageProfile field corresponds to the Storage Policy in VMware Cloud Director that you find under `Datacenter > your tenant > Storage > Storage policies`.

When you create a PV, it will appear under Named disks where you can find which VM it is connected to.

## Notes on `enableVirtualServiceSharedIP`

There are 3 possible scenarios for this setting:

- `enableVirtualServiceSharedIP: true` and `oneArm.enabled: false` **(default value)**

A service type load balancer with multiple ports creates virtual services that share an IP from the Edge external pool. The environment must support virtual service shared IP (VCD 10.4 or xxx flag in AVI load balancer).

- `enableVirtualServiceSharedIP: true` and `oneArm.enabled: true`

A service type load balancer with multiple ports creates virtual services that share an internal IP (usually 192.168.8.x) with a NAT rule to map an IP from the Edge external pool to the internal IP. The environment must support virtual service shared IP (VCD 10.4 or xxx flag in AVI load balancer).

- `enableVirtualServiceSharedIP: false` and `oneArm.enabled: true | false`

A service type load balancer with multiple ports creates virtual services with different internal IPs (usually 192.168.8.x) with NAT rules to map an IP from the Edge external pool to the internal IPs. Compatible with versions older than VCD 10.4.

## How are the charts created

There are no upstream charts available so these charts are created manually based on the upstream manifests.

The CSI and CPI are in separate upstream repo, we decided to merge them in a single `cloud-provider` app to be consistent with Openstack. The Helm charts are built based on the following resources:

* **CPI**: https://github.com/vmware/cloud-provider-for-cloud-director/tree/main/manifests
* **CSI**: https://github.com/vmware/cloud-director-named-disk-csi-driver/tree/main/manifests
