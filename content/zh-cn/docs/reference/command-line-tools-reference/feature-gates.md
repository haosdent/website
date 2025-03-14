---
title: 特性门控
weight: 10
content_type: concept
card:
  name: reference
  weight: 60
---

<!--
title: Feature Gates
weight: 10
content_type: concept
card:
  name: reference
  weight: 60
-->

<!-- overview -->
<!--
This page contains an overview of the various feature gates an administrator
can specify on different Kubernetes components.

See [feature stages](#feature-stages) for an explanation of the stages for a feature.
-->
本页详述了管理员可以在不同的 Kubernetes 组件上指定的各种特性门控。

关于特性各个阶段的说明，请参见[特性阶段](#feature-stages)。

<!-- body -->

<!--
## Overview

Feature gates are a set of key=value pairs that describe Kubernetes features.
You can turn these features on or off using the `--feature-gates` command line flag
on each Kubernetes component.
-->
## 概述 {#overview}

特性门控是描述 Kubernetes 特性的一组键值对。你可以在 Kubernetes 的各个组件中使用
`--feature-gates` 标志来启用或禁用这些特性。

<!--
Each Kubernetes component lets you enable or disable a set of feature gates that
are relevant to that component.
Use `-h` flag to see a full set of feature gates for all components.
To set feature gates for a component, such as kubelet, use the `--feature-gates`
flag assigned to a list of feature pairs:
-->
每个 Kubernetes 组件都支持启用或禁用与该组件相关的一组特性门控。
使用 `-h` 参数来查看所有组件支持的完整特性门控。
要为诸如 kubelet 之类的组件设置特性门控，请使用 `--feature-gates` 参数，
并向其传递一个特性设置键值对列表：

```shell
--feature-gates=...,GracefulNodeShutdown=true
```

<!--
The following tables are a summary of the feature gates that you can set on
different Kubernetes components.
-->
下表总结了在不同的 Kubernetes 组件上可以设置的特性门控。

<!--
- The "Since" column contains the Kubernetes release when a feature is introduced
  or its release stage is changed.
- The "Until" column, if not empty, contains the last Kubernetes release in which
  you can still use a feature gate.
- If a feature is in the Alpha or Beta state, you can find the feature listed
  in the [Alpha/Beta feature gate table](#feature-gates-for-alpha-or-beta-features).
- If a feature is stable you can find all stages for that feature listed in the
  [Graduated/Deprecated feature gate table](#feature-gates-for-graduated-or-deprecated-features).
- The [Graduated/Deprecated feature gate table](#feature-gates-for-graduated-or-deprecated-features)
  also lists deprecated and withdrawn features.
-->
- 引入特性或更改其发布阶段后，"开始（Since）" 列将包含 Kubernetes 版本。
- "结束（Until）" 列（如果不为空）包含最后一个 Kubernetes 版本，你仍可以在其中使用特性门控。
- 如果某个特性处于 Alpha 或 Beta 状态，你可以在
  [Alpha 和 Beta 特性门控表](#feature-gates-for-alpha-or-beta-features)中找到该特性。
- 如果某个特性处于稳定状态，
  你可以在[已毕业和废弃特性门控表](#feature-gates-for-graduated-or-deprecated-features)中找到该特性的所有阶段。
- [已毕业和废弃特性门控表](#feature-gates-for-graduated-or-deprecated-features)还列出了废弃的和已被移除的特性。

{{< note >}}
<!--
For a reference to old feature gates that are removed, please refer to
[feature gates removed](/docs/reference/command-line-tools-reference/feature-gates-removed/).
-->
有关已移除的原有特性门控的参考信息，
请参阅[已移除的特性门控](/zh-cn/docs/reference/command-line-tools-reference/feature-gates-removed/)。
{{< /note >}}

<!--
### Feature gates for Alpha or Beta features
-->
### Alpha 和 Beta 状态的特性门控  {#feature-gates-for-alpha-or-beta-features}

{{< table caption="处于 Alpha 或 Beta 状态的特性门控" >}}

<!--
| Feature | Default | Stage | Since | Until |
-->
| 特性    | 默认值  | 状态  | 开始（Since） | 结束（Until） |
|---------|---------|-------|---------------|---------------|
| `APIListChunking` | `false` | Alpha | 1.8 | 1.8 |
| `APIListChunking` | `true` | Beta | 1.9 | |
| `APIPriorityAndFairness` | `false` | Alpha | 1.18 | 1.19 |
| `APIPriorityAndFairness` | `true` | Beta | 1.20 | |
| `APIResponseCompression` | `false` | Alpha | 1.7 | 1.15 |
| `APIResponseCompression` | `true` | Beta | 1.16 | |
| `APIServerIdentity` | `false` | Alpha | 1.20 | |
| `APIServerTracing` | `false` | Alpha | 1.22 | |
| `AllowInsecureBackendProxy` | `true` | Beta | 1.17 | |
| `AnyVolumeDataSource` | `false` | Alpha | 1.18 | 1.23 |
| `AnyVolumeDataSource` | `true` | Beta | 1.24 | |
| `AppArmor` | `true` | Beta | 1.4 | |
| `CPUManager` | `false` | Alpha | 1.8 | 1.9 |
| `CPUManager` | `true` | Beta | 1.10 | |
| `CPUManagerPolicyAlphaOptions` | `false` | Alpha | 1.23 | |
| `CPUManagerPolicyBetaOptions` | `true` | Beta | 1.23 | |
| `CPUManagerPolicyOptions` | `false` | Alpha | 1.22 | 1.22 |
| `CPUManagerPolicyOptions` | `true` | Beta | 1.23 | |
| `CSIMigrationAzureFile` | `false` | Alpha | 1.15 | 1.20 |
| `CSIMigrationAzureFile` | `false` | Beta | 1.21 | 1.23 |
| `CSIMigrationAzureFile` | `true` | Beta | 1.24 | |
| `CSIMigrationPortworx` | `false` | Alpha | 1.23 | 1.24 |
| `CSIMigrationPortworx` | `false` | Beta | 1.25 | |
| `CSIMigrationRBD` | `false` | Alpha | 1.23 | |
| `CSIMigrationvSphere` | `false` | Alpha | 1.18 | 1.18 |
| `CSIMigrationvSphere` | `false` | Beta | 1.19 | 1.24 |
| `CSIMigrationvSphere` | `true` | Beta | 1.25 | |
| `CSINodeExpandSecret` | `false` | Alpha | 1.25 | |
| `CSIVolumeHealth` | `false` | Alpha | 1.21 | |
| `ContainerCheckpoint` | `false` | Alpha | 1.25 | |
| `ContextualLogging` | `false` | Alpha | 1.24 | |
| `CustomCPUCFSQuotaPeriod` | `false` | Alpha | 1.12 | |
| `CustomResourceValidationExpressions` | `false` | Alpha | 1.23 | 1.24 |
| `CustomResourceValidationExpressions` | `true` | Beta | 1.25 | |
| `DelegateFSGroupToCSIDriver` | `false` | Alpha | 1.22 | 1.22 |
| `DelegateFSGroupToCSIDriver` | `true` | Beta | 1.23 | |
| `DevicePlugins` | `false` | Alpha | 1.8 | 1.9 |
| `DevicePlugins` | `true` | Beta | 1.10 | |
| `DisableCloudProviders` | `false` | Alpha | 1.22 | |
| `DisableKubeletCloudCredentialProviders` | `false` | Alpha | 1.23 | |
| `DownwardAPIHugePages` | `false` | Alpha | 1.20 | 1.20 |
| `DownwardAPIHugePages` | `false` | Beta | 1.21 | 1.21 |
| `DownwardAPIHugePages` | `true` | Beta | 1.22 | |
| `EndpointSliceTerminatingCondition` | `false` | Alpha | 1.20 | 1.21 |
| `EndpointSliceTerminatingCondition` | `true` | Beta | 1.22 | |
| `ExpandedDNSConfig` | `false` | Alpha | 1.22 | |
| `ExperimentalHostUserNamespaceDefaulting` | `false` | Beta | 1.5 | |
| `GRPCContainerProbe` | `false` | Alpha | 1.23 | 1.23 |
| `GRPCContainerProbe` | `true` | Beta | 1.24 | |
| `GracefulNodeShutdown` | `false` | Alpha | 1.20 | 1.20 |
| `GracefulNodeShutdown` | `true` | Beta | 1.21 | |
| `GracefulNodeShutdownBasedOnPodPriority` | `false` | Alpha | 1.23 | 1.23 |
| `GracefulNodeShutdownBasedOnPodPriority` | `true` | Beta | 1.24 | |
| `HPAContainerMetrics` | `false` | Alpha | 1.20 | |
| `HPAScaleToZero` | `false` | Alpha | 1.16 | |
| `HonorPVReclaimPolicy` | `false` | Alpha | 1.23 |  |
| `InTreePluginAWSUnregister` | `false` | Alpha | 1.21 | |
| `InTreePluginAzureDiskUnregister` | `false` | Alpha | 1.21 | |
| `InTreePluginAzureFileUnregister` | `false` | Alpha | 1.21 | |
| `InTreePluginGCEUnregister` | `false` | Alpha | 1.21 | |
| `InTreePluginOpenStackUnregister` | `false` | Alpha | 1.21 | |
| `InTreePluginPortworxUnregister` | `false` | Alpha | 1.23 | |
| `InTreePluginRBDUnregister` | `false` | Alpha | 1.23 | |
| `InTreePluginvSphereUnregister` | `false` | Alpha | 1.21 | |
| `IPTablesOwnershipCleanup` | `false` | Alpha | 1.25 | |
| `JobMutableNodeSchedulingDirectives` | `true` | Beta | 1.23 | |
| `JobPodFailurePolicy` | `false` | Alpha | 1.25 | - |
| `JobReadyPods` | `false` | Alpha | 1.23 | 1.23 |
| `JobReadyPods` | `true` | Beta | 1.24 | |
| `JobTrackingWithFinalizers` | `false` | Alpha | 1.22 | 1.22 |
| `JobTrackingWithFinalizers` | `true` | Beta | 1.23 | |
| `KubeletCredentialProviders` | `false` | Alpha | 1.20 | 1.23 |
| `KubeletCredentialProviders` | `true` | Beta | 1.24 | |
| `KubeletInUserNamespace` | `false` | Alpha | 1.22 | |
| `KubeletPodResources` | `false` | Alpha | 1.13 | 1.14 |
| `KubeletPodResources` | `true` | Beta | 1.15 | |
| `KubeletPodResourcesGetAllocatable` | `false` | Alpha | 1.21 | 1.22 |
| `KubeletPodResourcesGetAllocatable` | `true` | Beta | 1.23 | |
| `KubeletTracing` | `false` | Alpha | 1.25 | |
| `LegacyServiceAccountTokenNoAutoGeneration` | `true` | Beta | 1.24 | |
| `LocalStorageCapacityIsolationFSQuotaMonitoring` | `false` | Alpha | 1.15 | 1.24 |
| `LocalStorageCapacityIsolationFSQuotaMonitoring` | `true` | Beta | 1.25 | |
| `LogarithmicScaleDown` | `false` | Alpha | 1.21 | 1.21 |
| `LogarithmicScaleDown` | `true` | Beta | 1.22 | |
| `MatchLabelKeysInPodTopologySpread` | `false` | Alpha | 1.25 | |
| `MaxUnavailableStatefulSet` | `false` | Alpha | 1.24 | |
| `MemoryManager` | `false` | Alpha | 1.21 | 1.21 |
| `MemoryManager` | `true` | Beta | 1.22 | |
| `MemoryQoS` | `false` | Alpha | 1.22 | |
| `MinDomainsInPodTopologySpread` | `false` | Alpha | 1.24 | 1.24 |
| `MinDomainsInPodTopologySpread` | `false` | Beta | 1.25 | |
| `MixedProtocolLBService` | `false` | Alpha | 1.20 | 1.23 |
| `MixedProtocolLBService` | `true` | Beta | 1.24 | |
| `MultiCIDRRangeAllocator` | `false` | Alpha | 1.25 | |
| `NetworkPolicyStatus` | `false` | Alpha | 1.24 |  |
| `NodeInclusionPolicyInPodTopologySpread` | `false` | Alpha | 1.25 | |
| `NodeOutOfServiceVolumeDetach` | `false` | Alpha | 1.24 | |
| `NodeSwap` | `false` | Alpha | 1.22 | |
| `OpenAPIEnums` | `false` | Alpha | 1.23 | 1.23 |
| `OpenAPIEnums` | `true` | Beta | 1.24 | |
| `OpenAPIV3` | `false` | Alpha | 1.23 | 1.23 |
| `OpenAPIV3` | `true` | Beta | 1.24 | |
| `PodAndContainerStatsFromCRI` | `false` | Alpha | 1.23 | |
| `PodDeletionCost` | `false` | Alpha | 1.21 | 1.21 |
| `PodDeletionCost` | `true` | Beta | 1.22 | |
| `PodDisruptionConditions` | `false` | Alpha | 1.25 | - |
| `PodHasNetworkCondition` | `false` | Alpha | 1.25 | |
| `ProbeTerminationGracePeriod` | `false` | Alpha | 1.21 | 1.21 |
| `ProbeTerminationGracePeriod` | `false` | Beta | 1.22 | 1.24 |
| `ProbeTerminationGracePeriod` | `true` | Beta | 1.25 | |
| `ProcMountType` | `false` | Alpha | 1.12 | |
| `ProxyTerminatingEndpoints` | `false` | Alpha | 1.22 | |
| `QOSReserved` | `false` | Alpha | 1.11 | |
| `ReadWriteOncePod` | `false` | Alpha | 1.22 | |
| `RecoverVolumeExpansionFailure` | `false` | Alpha | 1.23 | |
| `RemainingItemCount` | `false` | Alpha | 1.15 | 1.15 |
| `RemainingItemCount` | `true` | Beta | 1.16 | |
| `RetroactiveDefaultStorageClass` | `false` | Alpha | 1.25 | |
| `RotateKubeletServerCertificate` | `false` | Alpha | 1.7 | 1.11 |
| `RotateKubeletServerCertificate` | `true` | Beta | 1.12 | |
| `SELinuxMountReadWriteOncePod` | `false` | Alpha | 1.25 | |
| `SeccompDefault` | `false` | Alpha | 1.22 | 1.24 |
| `SeccompDefault` | `true` | Beta | 1.25 | |
| `ServerSideFieldValidation` | `false` | Alpha | 1.23 | 1.24 |
| `ServerSideFieldValidation` | `true` | Beta | 1.25 | |
| `ServiceIPStaticSubrange` | `false` | Alpha | 1.24 | 1.24 |
| `ServiceIPStaticSubrange` | `true` | Beta | 1.25 | |
| `ServiceInternalTrafficPolicy` | `false` | Alpha | 1.21 | 1.21 |
| `ServiceInternalTrafficPolicy` | `true` | Beta | 1.22 | |
| `SizeMemoryBackedVolumes` | `false` | Alpha | 1.20 | 1.21 |
| `SizeMemoryBackedVolumes` | `true` | Beta | 1.22 | |
| `StatefulSetAutoDeletePVC` | `false` | Alpha | 1.22 | |
| `StorageVersionAPI` | `false` | Alpha | 1.20 | |
| `StorageVersionHash` | `false` | Alpha | 1.14 | 1.14 |
| `StorageVersionHash` | `true` | Beta | 1.15 | |
| `TopologyAwareHints` | `false` | Alpha | 1.21 | 1.22 |
| `TopologyAwareHints` | `false` | Beta | 1.23 | 1.23 |
| `TopologyAwareHints` | `true` | Beta | 1.24 | |
| `TopologyManager` | `false` | Alpha | 1.16 | 1.17 |
| `TopologyManager` | `true` | Beta | 1.18 | |
| `UserNamespacesStatelessPodsSupport` | `false` | Alpha | 1.25 | |
| `VolumeCapacityPriority` | `false` | Alpha | 1.21 | - |
| `WinDSR` | `false` | Alpha | 1.14 | |
| `WinOverlay` | `false` | Alpha | 1.14 | 1.19 |
| `WinOverlay` | `true` | Beta | 1.20 | |
| `WindowsHostProcessContainers` | `false` | Alpha | 1.22 | 1.22 |
| `WindowsHostProcessContainers` | `true` | Beta | 1.23 | |
{{< /table >}}

<!--
### Feature gates for graduated or deprecated features
-->
### 已毕业和已废弃的特性门控  {#feature-gates-for-graduated-or-deprecated-features}

{{< table caption="已毕业或不推荐使用的特性门控" >}}

<!--
| Feature | Default | Stage | Since | Until |
-->
| 特性    | 默认值  | 状态  | 开始（Since） | 结束（Until） |
|---------|---------|-------|---------------|---------------|
| `AdvancedAuditing` | `false` | Alpha | 1.7 | 1.7 |
| `AdvancedAuditing` | `true` | Beta | 1.8 | 1.11 |
| `AdvancedAuditing` | `true` | GA | 1.12 | - |
| `CSIInlineVolume` | `false` | Alpha | 1.15 | 1.15 |
| `CSIInlineVolume` | `true` | Beta | 1.16 | 1.24 |
| `CSIInlineVolume` | `true` | GA | 1.25 | - |
| `CSIMigration` | `false` | Alpha | 1.14 | 1.16 |
| `CSIMigration` | `true` | Beta | 1.17 | 1.24 |
| `CSIMigration` | `true` | GA | 1.25 | - |
| `CSIMigrationAWS` | `false` | Alpha | 1.14 | 1.16 |
| `CSIMigrationAWS` | `false` | Beta | 1.17 | 1.22 |
| `CSIMigrationAWS` | `true` | Beta | 1.23 | 1.24 |
| `CSIMigrationAWS` | `true` | GA | 1.25 | - |
| `CSIMigrationAzureDisk` | `false` | Alpha | 1.15 | 1.18 |
| `CSIMigrationAzureDisk` | `false` | Beta | 1.19 | 1.22 |
| `CSIMigrationAzureDisk` | `true` | Beta | 1.23 | 1.23 |
| `CSIMigrationAzureDisk` | `true` | GA | 1.24 | |
| `CSIMigrationGCE` | `false` | Alpha | 1.14 | 1.16 |
| `CSIMigrationGCE` | `false` | Beta | 1.17 | 1.22 |
| `CSIMigrationGCE` | `true` | Beta | 1.23 | 1.24 |
| `CSIMigrationGCE` | `true` | GA | 1.25 | - |
| `CSIMigrationOpenStack` | `false` | Alpha | 1.14 | 1.17 |
| `CSIMigrationOpenStack` | `true` | Beta | 1.18 | 1.23 |
| `CSIMigrationOpenStack` | `true` | GA | 1.24 | |
| `CSIStorageCapacity` | `false` | Alpha | 1.19 | 1.20 |
| `CSIStorageCapacity` | `true` | Beta | 1.21 | 1.23 |
| `CSIStorageCapacity` | `true` | GA | 1.24 | - |
| `CSRDuration` | `true` | Beta | 1.22 | 1.23 |
| `CSRDuration` | `true` | GA | 1.24 | - |
| `ControllerManagerLeaderMigration` | `false` | Alpha | 1.21 | 1.21 |
| `ControllerManagerLeaderMigration` | `true` | Beta | 1.22 | 1.23 |
| `ControllerManagerLeaderMigration` | `true` | GA | 1.24 | - |
| `CronJobTimeZone` | `false` | Alpha | 1.24 | 1.24 |
| `CronJobTimeZone` | `true` | Beta | 1.25 | |
| `DaemonSetUpdateSurge` | `false` | Alpha | 1.21 | 1.21 |
| `DaemonSetUpdateSurge` | `true` | Beta | 1.22 | 1.24 |
| `DaemonSetUpdateSurge` | `true` | GA | 1.25 | - |
| `DefaultPodTopologySpread` | `false` | Alpha | 1.19 | 1.19 |
| `DefaultPodTopologySpread` | `true` | Beta | 1.20 | 1.23 |
| `DefaultPodTopologySpread` | `true` | GA | 1.24 | - |
| `DisableAcceleratorUsageMetrics` | `false` | Alpha | 1.19 | 1.19 |
| `DisableAcceleratorUsageMetrics` | `true` | Beta | 1.20 | 1.24 |
| `DisableAcceleratorUsageMetrics` | `true` | Beta | 1.25 |- |
| `DryRun` | `false` | Alpha | 1.12 | 1.12 |
| `DryRun` | `true` | Beta | 1.13 | 1.18 |
| `DryRun` | `true` | GA | 1.19 | - |
| `DynamicKubeletConfig` | `false` | Alpha | 1.4 | 1.10 |
| `DynamicKubeletConfig` | `true` | Beta | 1.11 | 1.21 |
| `DynamicKubeletConfig` | `false` | Deprecated | 1.22 | - |
| `EfficientWatchResumption` | `false` | Alpha | 1.20 | 1.20 |
| `EfficientWatchResumption` | `true` | Beta | 1.21 | 1.23 |
| `EfficientWatchResumption` | `true` | GA | 1.24 | - |
| `EphemeralContainers` | `false` | Alpha | 1.16 | 1.22 |
| `EphemeralContainers` | `true` | Beta | 1.23 | 1.24 |
| `EphemeralContainers` | `true` | GA | 1.25 | - |
| `ExecProbeTimeout` | `true` | GA | 1.20 | - |
| `ExpandCSIVolumes` | `false` | Alpha | 1.14 | 1.15 |
| `ExpandCSIVolumes` | `true` | Beta | 1.16 | 1.23 |
| `ExpandCSIVolumes` | `true` | GA | 1.24 | - |
| `ExpandInUsePersistentVolumes` | `false` | Alpha | 1.11 | 1.14 |
| `ExpandInUsePersistentVolumes` | `true` | Beta | 1.15 | 1.23 |
| `ExpandInUsePersistentVolumes` | `true` | GA | 1.24 | - |
| `ExpandPersistentVolumes` | `false` | Alpha | 1.8 | 1.10 |
| `ExpandPersistentVolumes` | `true` | Beta | 1.11 | 1.23 |
| `ExpandPersistentVolumes` | `true` | GA | 1.24 |- |
| `IdentifyPodOS` | `false` | Alpha | 1.23 | 1.23 |
| `IdentifyPodOS` | `true` | Beta | 1.24 | 1.24 |
| `IdentifyPodOS` | `true` | GA | 1.25 | - |
| `IndexedJob` | `false` | Alpha | 1.21 | 1.21 |
| `IndexedJob` | `true` | Beta | 1.22 | 1.23 |
| `IndexedJob` | `true` | GA | 1.24 | - |
| `LocalStorageCapacityIsolation` | `false` | Alpha | 1.7 | 1.9 |
| `LocalStorageCapacityIsolation` | `true` | Beta | 1.10 | 1.24 |
| `LocalStorageCapacityIsolation` | `true` | GA | 1.25 | - |
| `NetworkPolicyEndPort` | `false` | Alpha | 1.21 | 1.21 |
| `NetworkPolicyEndPort` | `true` | Beta | 1.22 | 1.24 |
| `NetworkPolicyEndPort` | `true` | GA | 1.25 | - |
| `NonPreemptingPriority` | `false` | Alpha | 1.15 | 1.18 |
| `NonPreemptingPriority` | `true` | Beta | 1.19 | 1.23 |
| `NonPreemptingPriority` | `true` | GA | 1.24 | - |
| `PodAffinityNamespaceSelector` | `false` | Alpha | 1.21 | 1.21 |
| `PodAffinityNamespaceSelector` | `true` | Beta | 1.22 | 1.23 |
| `PodAffinityNamespaceSelector` | `true` | GA | 1.24 | - |
| `PodOverhead` | `false` | Alpha | 1.16 | 1.17 |
| `PodOverhead` | `true` | Beta | 1.18 | 1.23 |
| `PodOverhead` | `true` | GA | 1.24 | - |
| `PodSecurity` | `false` | Alpha | 1.22 | 1.22 |
| `PodSecurity` | `true` | Beta | 1.23 | 1.24 |
| `PodSecurity` | `true` | GA | 1.25 | |
| `PreferNominatedNode` | `false` | Alpha | 1.21 | 1.21 |
| `PreferNominatedNode` | `true` | Beta | 1.22 | 1.23 |
| `PreferNominatedNode` | `true` | GA | 1.24 | - |
| `RemoveSelfLink` | `false` | Alpha | 1.16 | 1.19 |
| `RemoveSelfLink` | `true` | Beta | 1.20 | 1.23 |
| `RemoveSelfLink` | `true` | GA | 1.24 | - |
| `ServerSideApply` | `false` | Alpha | 1.14 | 1.15 |
| `ServerSideApply` | `true` | Beta | 1.16 | 1.21 |
| `ServerSideApply` | `true` | GA | 1.22 | - |
| `ServiceLBNodePortControl` | `false` | Alpha | 1.20 | 1.21 |
| `ServiceLBNodePortControl` | `true` | Beta | 1.22 | 1.23 |
| `ServiceLBNodePortControl` | `true` | GA | 1.24 | - |
| `ServiceLoadBalancerClass` | `false` | Alpha | 1.21 | 1.21 |
| `ServiceLoadBalancerClass` | `true` | Beta | 1.22 | 1.23 |
| `ServiceLoadBalancerClass` | `true` | GA | 1.24 | - |
| `StatefulSetMinReadySeconds` | `false` | Alpha | 1.22 | 1.22 |
| `StatefulSetMinReadySeconds` | `true` | Beta | 1.23 | 1.24 |
| `StatefulSetMinReadySeconds` | `true` | GA | 1.25 | - |
| `SuspendJob` | `false` | Alpha | 1.21 | 1.21 |
| `SuspendJob` | `true` | Beta | 1.22 | 1.23 |
| `SuspendJob` | `true` | GA | 1.24 | - |
| `WatchBookmark` | `false` | Alpha | 1.15 | 1.15 |
| `WatchBookmark` | `true` | Beta | 1.16 | 1.16 |
| `WatchBookmark` | `true` | GA | 1.17 | - |
{{< /table >}}

<!--
## Using a feature

### Feature stages
-->
## 使用特性   {#using-a-feature}

### 特性阶段    {#feature-stages}

<!--
A feature can be in *Alpha*, *Beta* or *GA* stage.
An *Alpha* feature means:
-->
处于 **Alpha** 、**Beta** 、 **GA** 阶段的特性。

**Alpha** 特性代表：

<!--
* Disabled by default.
* Might be buggy. Enabling the feature may expose bugs.
* Support for feature may be dropped at any time without notice.
* The API may change in incompatible ways in a later software release without notice.
* Recommended for use only in short-lived testing clusters, due to increased
  risk of bugs and lack of long-term support.
-->
* 默认禁用。
* 可能有错误，启用此特性可能会导致错误。
* 随时可能删除对此特性的支持，恕不另行通知。
* 在以后的软件版本中，API 可能会以不兼容的方式更改，恕不另行通知。
* 建议将其仅用于短期测试中，因为开启特性会增加错误的风险，并且缺乏长期支持。

<!--
A *Beta* feature means:
-->
**Beta** 特性代表：

<!--
* Enabled by default.
* The feature is well tested. Enabling the feature is considered safe.
* Support for the overall feature will not be dropped, though details may change.
* The schema and/or semantics of objects may change in incompatible ways in a
  subsequent beta or stable release. When this happens, we will provide instructions
  for migrating to the next version. This may require deleting, editing, and
  re-creating API objects. The editing process may require some thought.
  This may require downtime for applications that rely on the feature.
* Recommended for only non-business-critical uses because of potential for
  incompatible changes in subsequent releases. If you have multiple clusters
  that can be upgraded independently, you may be able to relax this restriction.
-->
* 默认启用。
* 该特性已经经过良好测试。启用该特性是安全的。
* 尽管详细信息可能会更改，但不会放弃对整体特性的支持。
* 对象的架构或语义可能会在随后的 Beta 或稳定版本中以不兼容的方式更改。
  当发生这种情况时，我们将提供迁移到下一版本的说明。此特性可能需要删除、编辑和重新创建 API 对象。
  编辑过程可能需要慎重操作，因为这可能会导致依赖该特性的应用程序停机。
* 推荐仅用于非关键业务用途，因为在后续版本中可能会发生不兼容的更改。如果你具有多个可以独立升级的，则可以放宽此限制。

{{< note >}}
<!--
Please do try *Beta* features and give feedback on them!
After they exit beta, it may not be practical for us to make more changes.
-->
请试用 **Beta** 特性并提供相关反馈！
一旦特性结束 Beta 状态，我们就不太可能再对特性进行大幅修改。
{{< /note >}}

<!--
A *General Availability* (GA) feature is also referred to as a *stable* feature. It means:
-->
**General Availability** (GA) 特性也称为 **稳定** 特性，**GA** 特性代表着：

<!--
* The feature is always enabled; you cannot disable it.
* The corresponding feature gate is no longer needed.
* Stable versions of features will appear in released software for many subsequent versions.
-->
* 此特性会一直启用；你不能禁用它。
* 不再需要相应的特性门控。
* 对于许多后续版本，特性的稳定版本将出现在发行的软件中。

<!--
## List of feature gates {#feature-gates}

Each feature gate is designed for enabling/disabling a specific feature:
-->

### 特性门控列表 {#feature-gates}

每个特性门控均用于启用或禁用某个特定的特性：

<!--
- `APIListChunking`: Enable the API clients to retrieve (`LIST` or `GET`)
  resources from API server in chunks.
- `APIPriorityAndFairness`: Enable managing request concurrency with
  prioritization and fairness at each server. (Renamed from `RequestManagement`)
- `APIResponseCompression`: Compress the API responses for `LIST` or `GET` requests.
- `APIServerIdentity`: Assign each API server an ID in a cluster.
- `APIServerTracing`: Add support for distributed tracing in the API server.
  See [Traces for Kubernetes System Components](/docs/concepts/cluster-administration/system-traces)
  for more details.
-->
- `APIListChunking`：启用 API 客户端以块的形式从 API 服务器检索（“LIST” 或 “GET”）资源。
- `APIPriorityAndFairness`：在每个服务器上启用优先级和公平性来管理请求并发（由 `RequestManagement` 重命名而来）。
- `APIResponseCompression`：压缩 “LIST” 或 “GET” 请求的 API 响应。
- `APIServerIdentity`：为集群中的每个 API 服务器赋予一个 ID。
- `APIServerTracing`：为集群中的每个 API 服务器添加对分布式跟踪的支持。
  参阅[针对 Kubernetes 系统组件的追踪](/zh-cn/docs/concepts/cluster-administration/system-traces/)
  获取更多详细信息。
<!--
- `AdvancedAuditing`: Enable [advanced auditing](/docs/tasks/debug/debug-cluster/audit/#advanced-audit)
- `AllowInsecureBackendProxy`: Enable the users to skip TLS verification of
  kubelets on Pod log requests.
- `AnyVolumeDataSource`: Enable use of any custom resource as the `DataSource` of a
  {{< glossary_tooltip text="PVC" term_id="persistent-volume-claim" >}}.
- `AppArmor`: Enable use of AppArmor mandatory access control for Pods running on Linux nodes.
  See [AppArmor Tutorial](/docs/tutorials/security/apparmor/) for more details.
-->
- `AdvancedAuditing`：启用[高级审计功能](/zh-cn/docs/tasks/debug/debug-cluster/audit/#advanced-audit)。
- `AllowExtTrafficLocalEndpoints`：启用服务用于将外部请求路由到节点本地终端。
- `AnyVolumeDataSource`：允许使用任何自定义的资源来做作为
  {{< glossary_tooltip text="PVC" term_id="persistent-volume-claim" >}} 中的 `DataSource`。
- `AppArmor`：在 Linux 节点上为 Pod 启用 AppArmor 机制的强制访问控制。
  请参见 [AppArmor 教程](/zh-cn/docs/tutorials/security/apparmor/)获取详细信息。
<!--
- `ContainerCheckpoint`: Enables the kubelet `checkpoint` API.
  See [Kubelet Checkpoint API](/docs/reference/node/kubelet-checkpoint-api/) for more details.
- `ControllerManagerLeaderMigration`: Enables Leader Migration for
  [kube-controller-manager](/docs/tasks/administer-cluster/controller-manager-leader-migration/#initial-leader-migration-configuration) and
  [cloud-controller-manager](/docs/tasks/administer-cluster/controller-manager-leader-migration/#deploy-cloud-controller-manager)
  which allows a cluster operator to live migrate
  controllers from the kube-controller-manager into an external controller-manager
  (e.g. the cloud-controller-manager) in an HA cluster without downtime.
-->
- `ContainerCheckpoint`：启用 kubelet `checkpoint` API。
  参阅 [Kubelet Checkpoint API](/zh-cn/docs/reference/node/kubelet-checkpoint-api/) 获取更多详细信息。
- `ControllerManagerLeaderMigration`：为
  [kube-controller-manager](/zh-cn/docs/tasks/administer-cluster/controller-manager-leader-migration/#initial-leader-migration-configuration) 和
  [cloud-controller-manager](/zh-cn/docs/tasks/administer-cluster/controller-manager-leader-migration/#deploy-cloud-controller-manager)
  启用 Leader 迁移，它允许集群管理者在没有停机的高可用集群环境下，实时把 kube-controller-manager
  迁移到外部的 controller-manager (例如 cloud-controller-manager) 中。
<!--
- `CPUManager`: Enable container level CPU affinity support, see
  [CPU Management Policies](/docs/tasks/administer-cluster/cpu-management-policies/).
- `CPUManagerPolicyAlphaOptions`: This allows fine-tuning of CPUManager policies,
  experimental, Alpha-quality options
  This feature gate guards *a group* of CPUManager options whose quality level is alpha.
  This feature gate will never graduate to beta or stable.
- `CPUManagerPolicyBetaOptions`: This allows fine-tuning of CPUManager policies,
  experimental, Beta-quality options
  This feature gate guards *a group* of CPUManager options whose quality level is beta.
  This feature gate will never graduate to stable.
- `CPUManagerPolicyOptions`: Allow fine-tuning of CPUManager policies.
-->
- `CPUManager`：启用容器级别的 CPU 亲和性支持，有关更多详细信息，请参见
  [CPU 管理策略](/zh-cn/docs/tasks/administer-cluster/cpu-management-policies/)。
- `CPUManagerPolicyAlphaOptions`：允许对 CPUManager 策略进行微调，针对试验性的、Alpha 质量级别的选项。
  此特性门控用来保护一组质量级别为 Alpha 的 CPUManager 选项。
  此特性门控永远不会被升级为 Beta 或者稳定版本。
- `CPUManagerPolicyBetaOptions`：允许对 CPUManager 策略进行微调，针对试验性的、Beta 质量级别的选项。
  此特性门控用来保护一组质量级别为 Beta 的 CPUManager 选项。
  此特性门控永远不会被升级为稳定版本。
- `CPUManagerPolicyOptions`：允许微调 CPU 管理策略。
<!--
- `CSIInlineVolume`: Enable CSI Inline volumes support for pods.
- `CSIMigration`: Enables shims and translation logic to route volume
  operations from in-tree plugins to corresponding pre-installed CSI plugins
-->
- `CSIInlineVolume`：为 Pod 启用 CSI 内联卷支持。
- `CSIMigration`：确保封装和转换逻辑能够将卷操作从内嵌插件路由到相应的预安装 CSI 插件。
<!--
- `CSIMigrationAWS`: Enables shims and translation logic to route volume
  operations from the AWS-EBS in-tree plugin to EBS CSI plugin. Supports
  falling back to in-tree EBS plugin for mount operations to nodes that have
  the feature disabled or that do not have EBS CSI plugin installed and
  configured. Does not support falling back for provision operations, for those
  the CSI plugin must be installed and configured.
-->
- `CSIMigrationAWS`：确保填充和转换逻辑能够将卷操作从 AWS-EBS 内嵌插件路由到 EBS CSI 插件。
  如果节点禁用了此特性门控或者未安装和配置 EBS CSI 插件，支持回退到内嵌 EBS 插件来执行卷挂载操作。
  不支持回退到这些插件来执行卷制备操作，因为需要安装并配置 CSI 插件。
<!--
- `CSIMigrationAzureDisk`: Enables shims and translation logic to route volume
  operations from the Azure-Disk in-tree plugin to AzureDisk CSI plugin.
  Supports falling back to in-tree AzureDisk plugin for mount operations to
  nodes that have the feature disabled or that do not have AzureDisk CSI plugin
  installed and configured. Does not support falling back for provision
  operations, for those the CSI plugin must be installed and configured.
  Requires CSIMigration feature flag enabled.
-->
- `CSIMigrationAzureDisk`：确保填充和转换逻辑能够将卷操作从 AzureDisk 内嵌插件路由到
  Azure 磁盘 CSI 插件。对于禁用了此特性的节点或者没有安装并配置 AzureDisk CSI
  插件的节点，支持回退到内嵌（in-tree）AzureDisk 插件来执行磁盘挂载操作。
  不支持回退到内嵌插件来执行磁盘制备操作，因为对应的 CSI 插件必须已安装且正确配置。
  此特性需要启用 CSIMigration 特性标志。
<!--
- `CSIMigrationAzureFile`: Enables shims and translation logic to route volume
  operations from the Azure-File in-tree plugin to AzureFile CSI plugin.
  Supports falling back to in-tree AzureFile plugin for mount operations to
  nodes that have the feature disabled or that do not have AzureFile CSI plugin
  installed and configured. Does not support falling back for provision
  operations, for those the CSI plugin must be installed and configured.
  Requires CSIMigration feature flag enabled.
-->
- `CSIMigrationAzureFile`：确保封装和转换逻辑能够将卷操作从 AzureFile 内嵌插件路由到
  AzureFile CSI 插件。对于禁用了此特性的节点或者没有安装并配置 AzureFile CSI
  插件的节点，支持回退到内嵌（in-tree）AzureFile 插件来执行卷挂载操作。
  不支持回退到内嵌插件来执行卷制备操作，因为对应的 CSI 插件必须已安装且正确配置。
  此特性需要启用 CSIMigration 特性标志。
<!--
- `CSIMigrationGCE`: Enables shims and translation logic to route volume
  operations from the GCE-PD in-tree plugin to PD CSI plugin. Supports falling
  back to in-tree GCE plugin for mount operations to nodes that have the
  feature disabled or that do not have PD CSI plugin installed and configured.
  Does not support falling back for provision operations, for those the CSI
  plugin must be installed and configured. Requires CSIMigration feature flag
  enabled.
-->
- `CSIMigrationGCE`：启用填充和转换逻辑，将卷操作从 GCE-PD 内嵌插件路由到
  PD CSI 插件。对于禁用了此特性的节点或者没有安装并配置 PD CSI 插件的节点，
  支持回退到内嵌（in-tree）GCE 插件来执行挂载操作。
  不支持回退到内嵌插件来执行制备操作，因为对应的 CSI 插件必须已安装且正确配置。
  此特性需要启用 CSIMigration 特性标志。
<!--
- `CSIMigrationOpenStack`: Enables shims and translation logic to route volume
  operations from the Cinder in-tree plugin to Cinder CSI plugin. Supports
  falling back to in-tree Cinder plugin for mount operations to nodes that have
  the feature disabled or that do not have Cinder CSI plugin installed and
  configured. Does not support falling back for provision operations, for those
  the CSI plugin must be installed and configured. Requires CSIMigration
  feature flag enabled.
-->
- `CSIMigrationOpenStack`：确保填充和转换逻辑能够将卷操作从 Cinder 内嵌插件路由到
  Cinder CSI 插件。对于禁用了此特性的节点或者没有安装并配置 Cinder CSI 插件的节点，
  支持回退到内嵌（in-tree）Cinder 插件来执行挂载操作。
  不支持回退到内嵌插件来执行制备操作，因为对应的 CSI 插件必须已安装且正确配置。
  此磁特性需要启用 CSIMigration 特性标志。
<!--
- `csiMigrationRBD`: Enables shims and translation logic to route volume
  operations from the RBD in-tree plugin to Ceph RBD CSI plugin. Requires
  CSIMigration and csiMigrationRBD feature flags enabled and Ceph CSI plugin
  installed and configured in the cluster. This flag has been deprecated in
  favor of the `InTreePluginRBDUnregister` feature flag which prevents the registration of
  in-tree RBD plugin.
-->
- `csiMigrationRBD`：启用填充和转换逻辑，将卷操作从 RBD 的内嵌插件路由到 Ceph RBD
  CSI 插件。此特性要求 CSIMigration 和 csiMigrationRBD 特性标志均被启用，
  且集群中安装并配置了 Ceph CSI 插件。此标志已被弃用，以鼓励使用
  `InTreePluginRBDUnregister` 特性标志。后者会禁止注册内嵌的 RBD 插件。
<!--
- `CSIMigrationvSphere`: Enables shims and translation logic to route volume operations
  from the vSphere in-tree plugin to vSphere CSI plugin. Supports falling back
  to in-tree vSphere plugin for mount operations to nodes that have the feature
  disabled or that do not have vSphere CSI plugin installed and configured.
  Does not support falling back for provision operations, for those the CSI
  plugin must be installed and configured. Requires CSIMigration feature flag
  enabled.
-->
- `CSIMigrationvSphere`：允许封装和转换逻辑将卷操作从 vSphere 内嵌插件路由到
  vSphere CSI 插件。如果节点禁用了此特性门控或者未安装和配置 vSphere CSI 插件，
  则支持回退到 vSphere 内嵌插件来执行挂载操作。
  不支持回退到内嵌插件来执行制备操作，因为对应的 CSI 插件必须已安装且正确配置。
  这需要启用 CSIMigration 特性标志。
<!--
- `CSIMigrationPortworx`: Enables shims and translation logic to route volume operations
  from the Portworx in-tree plugin to Portworx CSI plugin.
  Requires Portworx CSI driver to be installed and configured in the cluster.
-->
- `CSIMigrationPortworx`：启用填充和转换逻辑，将卷操作从 Portworx 内嵌插件路由到
  Portworx CSI 插件。需要在集群中安装并配置 Portworx CSI 插件.
<!--
- `CSINodeExpandSecret`: Enable passing secret authentication data to a CSI driver for use
   during a `NodeExpandVolume` CSI operation.
- `CSIStorageCapacity`: Enables CSI drivers to publish storage capacity information
  and the Kubernetes scheduler to use that information when scheduling pods. See
  [Storage Capacity](/docs/concepts/storage/storage-capacity/).
  Check the [`csi` volume type](/docs/concepts/storage/volumes/#csi) documentation for more details.
-->
- `CSINodeExpandSecret`：允许在 `NodeExpandVolume` CSI 操作期间将 Secret
  身份验证数据传递到 CSI 驱动以供后者使用。
- `CSIStorageCapacity`：使 CSI 驱动程序可以发布存储容量信息，并使 Kubernetes
  调度程序在调度 Pod 时使用该信息。参见[存储容量](/zh-cn/docs/concepts/storage/storage-capacity/)。
  详情请参见 [`csi` 卷类型](/zh-cn/docs/concepts/storage/volumes/#csi)。
<!--
- `CSIVolumeHealth`: Enable support for CSI volume health monitoring on node.
- `CSRDuration`: Allows clients to request a duration for certificates issued
  via the Kubernetes CSR API.
- `ContextualLogging`: When you enable this feature gate, Kubernetes components that support
   contextual logging add extra detail to log output.
- `ControllerManagerLeaderMigration`: Enables leader migration for
  `kube-controller-manager` and `cloud-controller-manager`.
- `CronJobTimeZone`: Allow the use of the `timeZone` optional field in [CronJobs](/docs/concepts/workloads/controllers/cron-jobs/)
-->
- `CSIVolumeHealth`：启用对节点上的 CSI volume 运行状况监控的支持
- `CSRDuration`：允许客户端来通过请求 Kubernetes CSR API 签署的证书的持续时间。
- `ContextualLogging`：当你启用这个特性门控，支持日志上下文记录的 Kubernetes
  组件会为日志输出添加额外的详细内容。
- `ControllerManagerLeaderMigration`：为 `kube-controller-manager` 和 `cloud-controller-manager`
  开启领导者迁移功能。
- `CronJobTimeZone`：允许在 [CronJobs](/zh-cn/docs/concepts/workloads/controllers/cron-jobs/)
  中使用 `timeZone` 可选字段。
<!--
- `CustomCPUCFSQuotaPeriod`: Enable nodes to change `cpuCFSQuotaPeriod` in
  [kubelet config](/docs/tasks/administer-cluster/kubelet-config-file/).
- `CustomResourceValidationExpressions`: Enable expression language validation in CRD
  which will validate customer resource based on validation rules written in
  the `x-kubernetes-validations` extension.
-->
- `CustomCPUCFSQuotaPeriod`：使节点能够更改
  [kubelet 配置](/zh-cn/docs/tasks/administer-cluster/kubelet-config-file/)中的 `cpuCFSQuotaPeriod`。
- `CustomResourceValidationExpressions`：启用 CRD 中的表达式语言合法性检查，
  基于 `x-kubernetes-validations` 扩展中所书写的合法性检查规则来验证定制资源。
<!--
- `DaemonSetUpdateSurge`: Enables the DaemonSet workloads to maintain
  availability during update per node.
  See [Perform a Rolling Update on a DaemonSet](/docs/tasks/manage-daemon/update-daemon-set/).
-->
- `DaemonSetUpdateSurge`：使 DaemonSet 工作负载在每个节点的更新期间保持可用性。
  参阅[对 DaemonSet 执行滚动更新](/zh-cn/docs/tasks/manage-daemon/update-daemon-set/)。
<!--
- `DefaultPodTopologySpread`: Enables the use of `PodTopologySpread` scheduling plugin to do
  [default spreading](/docs/concepts/scheduling-eviction/topology-spread-constraints/#internal-default-constraints).
- `DelegateFSGroupToCSIDriver`: If supported by the CSI driver, delegates the
  role of applying `fsGroup` from a Pod's `securityContext` to the driver by
  passing `fsGroup` through the NodeStageVolume and NodePublishVolume CSI calls.
- `DevicePlugins`: Enable the [device-plugins](/docs/concepts/extend-kubernetes/compute-storage-net/device-plugins/)
  based resource provisioning on nodes.
- `DisableAcceleratorUsageMetrics`:
  [Disable accelerator metrics collected by the kubelet](/docs/concepts/cluster-administration/system-metrics/#disable-accelerator-metrics).
-->
- `DefaultPodTopologySpread`：启用 `PodTopologySpread` 调度插件来完成
  [默认的调度传播](/zh-cn/docs/concepts/scheduling-eviction/topology-spread-constraints/#internal-default-constraints)。
- `DelegateFSGroupToCSIDriver`：如果 CSI 驱动程序支持，则通过 NodeStageVolume 和
  NodePublishVolume CSI 调用传递 `fsGroup`，将应用 `fsGroup` 从 Pod 的
  `securityContext` 的角色委托给驱动。
- `DevicePlugins`：在节点上启用基于[设备插件](/zh-cn/docs/concepts/extend-kubernetes/compute-storage-net/device-plugins/)的资源制备。
- `DisableAcceleratorUsageMetrics`：
  [禁用 kubelet 收集加速器指标](/zh-cn/docs/concepts/cluster-administration/system-metrics/#disable-accelerator-metrics)。
<!--
- `DisableCloudProviders`: Disables any functionality in `kube-apiserver`,
  `kube-controller-manager` and `kubelet` related to the `--cloud-provider`
  component flag.
- `DisableKubeletCloudCredentialProviders`: Disable the in-tree functionality in kubelet
  to authenticate to a cloud provider container registry for image pull credentials.
- `DownwardAPIHugePages`: Enables usage of hugepages in
  [downward API](/docs/tasks/inject-data-application/downward-api-volume-expose-pod-information).
- `DryRun`: Enable server-side [dry run](/docs/reference/using-api/api-concepts/#dry-run) requests
  so that validation, merging, and mutation can be tested without committing.
-->
- `DisableCloudProviders`：禁用 `kube-apiserver`，`kube-controller-manager` 和
  `kubelet` 组件的 `--cloud-provider` 标志相关的所有功能。
- `DisableKubeletCloudCredentialProviders`：禁用 kubelet 中为拉取镜像内置的凭据机制，
  该凭据用于向某云提供商的容器镜像仓库执行身份认证。
- `DownwardAPIHugePages`：
  允许在[下行（Downward）API](/zh-cn/docs/tasks/inject-data-application/downward-api-volume-expose-pod-information)
  中使用巨页信息。
- `DryRun`：启用在服务器端对请求进行[试运行（Dry Run）](/zh-cn/docs/reference/using-api/api-concepts/#dry-run)，
  以便测试验证、合并和修改，同时避免提交更改。
<!--
- `DynamicKubeletConfig`: Enable the dynamic configuration of kubelet. The
  feature is no longer supported outside of supported skew policy. The feature
  gate was removed from kubelet in 1.24. See [Reconfigure kubelet](/docs/tasks/administer-cluster/reconfigure-kubelet/).
-->
- `DynamicKubeletConfig`：启用 kubelet 的动态配置。
  除偏差策略场景外，不再支持该功能。该特性门控在 kubelet 1.24 版本中已被移除。
  请参阅[重新配置 kubelet](/zh-cn/docs/tasks/administer-cluster/reconfigure-kubelet/)。
<!--
- `EndpointSliceTerminatingCondition`: Enables EndpointSlice `terminating` and `serving`
   condition fields.
- `EfficientWatchResumption`: Allows for storage-originated bookmark (progress
  notify) events to be delivered to the users. This is only applied to watch operations.
-->
- `EndpointSliceTerminatingCondition`：允许使用 EndpointSlice 的 `terminating` 和
  `serving` 状况字段。
- `EfficientWatchResumption`：允许将存储发起的书签（进度通知）事件传递给用户。
  这仅适用于监视操作。
<!--
- `EphemeralContainers`: Enable the ability to add
  {{< glossary_tooltip text="ephemeral containers" term_id="ephemeral-container" >}}
  to running pods.
- `ExecProbeTimeout`: Ensure kubelet respects exec probe timeouts.
  This feature gate exists in case any of your existing workloads depend on a
  now-corrected fault where Kubernetes ignored exec probe timeouts. See
  [readiness probes](/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).
-->
- `EphemeralContainers`：启用添加
  {{< glossary_tooltip text="临时容器" term_id="ephemeral-container" >}}
  到正在运行的 Pod 的特性。
- `ExecProbeTimeout`：确保 kubelet 会遵从 exec 探针的超时值设置。
  此特性门控的主要目的是方便你处理现有的、依赖于已被修复的缺陷的工作负载；
  该缺陷导致 Kubernetes 会忽略 exec 探针的超时值设置。
  参阅[就绪态探针](/zh-cn/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).
<!--
- `ExpandCSIVolumes`: Enable the expanding of CSI volumes.
- `ExpandedDNSConfig`: Enable kubelet and kube-apiserver to allow more DNS
  search paths and longer list of DNS search paths. This feature requires container
  runtime support(Containerd: v1.5.6 or higher, CRI-O: v1.22 or higher). See
  [Expanded DNS Configuration](/docs/concepts/services-networking/dns-pod-service/#expanded-dns-configuration).
- `ExpandInUsePersistentVolumes`: Enable expanding in-use PVCs. See
  [Resizing an in-use PersistentVolumeClaim](/docs/concepts/storage/persistent-volumes/#resizing-an-in-use-persistentvolumeclaim).
- `ExpandPersistentVolumes`: Enable the expanding of persistent volumes. See
  [Expanding Persistent Volumes Claims](/docs/concepts/storage/persistent-volumes/#expanding-persistent-volumes-claims).
-->
- `ExpandCSIVolumes`：启用扩展 CSI 卷。
- `ExpandedDNSConfig`：在 kubelet 和 kube-apiserver 上启用后，
  允许使用更多的 DNS 搜索域和搜索域列表。此功能特性需要容器运行时
  （Containerd：v1.5.6 或更高，CRI-O：v1.22 或更高）的支持。
  参阅[扩展 DNS 配置](/zh-cn/docs/concepts/services-networking/dns-pod-service/#expanded-dns-configuration).
- `ExpandInUsePersistentVolumes`：启用扩充使用中的 PVC 的尺寸。
  请查阅[调整使用中的 PersistentVolumeClaim 的大小](/zh-cn/docs/concepts/storage/persistent-volumes/#resizing-an-in-use-persistentvolumeclaim)。
- `ExpandPersistentVolumes`：允许扩充持久卷。
  请查阅[扩展持久卷申领](/zh-cn/docs/concepts/storage/persistent-volumes/#expanding-persistent-volumes-claims)。
<!--
- `ExperimentalHostUserNamespaceDefaulting`: Enabling the defaulting user
  namespace to host. This is for containers that are using other host namespaces,
  host mounts, or containers that are privileged or using specific non-namespaced
  capabilities (e.g. `MKNODE`, `SYS_MODULE` etc.). This should only be enabled
  if user namespace remapping is enabled in the Docker daemon.
- `GracefulNodeShutdown`: Enables support for graceful shutdown in kubelet.
  During a system shutdown, kubelet will attempt to detect the shutdown event
  and gracefully terminate pods running on the node. See
  [Graceful Node Shutdown](/docs/concepts/architecture/nodes/#graceful-node-shutdown)
  for more details.
-->
- `ExperimentalHostUserNamespaceDefaulting`：启用主机默认的用户名字空间。
  这适用于使用其他主机名字空间、主机安装的容器，或具有特权或使用特定的非名字空间功能
  （例如 MKNODE、SYS_MODULE 等）的容器。
  如果在 Docker 守护程序中启用了用户名字空间重新映射，则启用此选项。
- `GracefulNodeShutdown`：在 kubelet 中启用体面地关闭节点的支持。
  在系统关闭时，kubelet 会尝试监测该事件并体面地终止节点上运行的 Pod。
  参阅[体面地关闭节点](/zh-cn/docs/concepts/architecture/nodes/#graceful-node-shutdown)以了解更多细节。
<!--
- `GracefulNodeShutdownBasedOnPodPriority`: Enables the kubelet to check Pod priorities
  when shutting down a node gracefully.
- `GRPCContainerProbe`: Enables the gRPC probe method for {Liveness,Readiness,Startup}Probe.
  See [Configure Liveness, Readiness and Startup Probes](/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#define-a-grpc-liveness-probe).
- `HonorPVReclaimPolicy`: Honor persistent volume reclaim policy when it is `Delete` irrespective of PV-PVC deletion ordering.
  For more details, check the
  [PersistentVolume deletion protection finalizer](/docs/concepts/storage/persistent-volumes/#persistentvolume-deletion-protection-finalizer)
  documentation.
-->
- `GracefulNodeShutdownBasedOnPodPriority`：允许 kubelet 在体面终止节点时检查
  Pod 的优先级。
- `GRPCContainerProbe`：为 LivenessProbe、ReadinessProbe、StartupProbe 启用 gRPC 探针。
  参阅[配置活跃态、就绪态和启动探针](/zh-cn/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#define-a-grpc-liveness-probe)。
- `HonorPVReclaimPolicy`：无论 PV 和 PVC 的删除顺序如何，当持久卷申领的策略为 `Delete`
  时，确保这种策略得到处理。
  更多详细信息，请参阅 [PersistentVolume 删除保护 finalizer](/zh-cn/docs/concepts/storage/persistent-volumes/#persistentvolume-deletion-protection-finalizer) 文档。
<!--
- `HPAContainerMetrics`: Enable the `HorizontalPodAutoscaler` to scale based on
  metrics from individual containers in target pods.
- `HPAScaleToZero`: Enables setting `minReplicas` to 0 for `HorizontalPodAutoscaler`
  resources when using custom or external metrics.
-->
- `HPAContainerMetrics`：允许 `HorizontalPodAutoscaler` 基于目标 Pods 中各容器的度量值来执行扩缩操作。
- `HPAScaleToZero`：使用自定义指标或外部指标时，可将 `HorizontalPodAutoscaler`
  资源的 `minReplicas` 设置为 0。
<!--
- `IPTablesOwnershipCleanup`: This causes kubelet to no longer create legacy IPTables rules.
-->
- `IPTablesOwnershipCleanup`：这使得 kubelet 不再创建传统的 IPTables 规则。
<!--
- `IdentifyPodOS`: Allows the Pod OS field to be specified. This helps in identifying
  the OS of the pod authoritatively during the API server admission time.
  In Kubernetes {{< skew currentVersion >}}, the allowed values for the `pod.spec.os.name`
  are `windows` and `linux`.
- `IndexedJob`: Allows the [Job](/docs/concepts/workloads/controllers/job/)
  controller to manage Pod completions per completion index.
- `InTreePluginAWSUnregister`: Stops registering the aws-ebs in-tree plugin in kubelet
  and volume controllers.
- `InTreePluginAzureDiskUnregister`: Stops registering the azuredisk in-tree plugin in kubelet
  and volume controllers.
- `InTreePluginAzureFileUnregister`: Stops registering the azurefile in-tree plugin in kubelet
  and volume controllers.
-->
- `IdentifyPodOS`：允许设置 Pod 的 OS 字段。这一设置有助于在 API 服务器准入期间确定性地辨识
  Pod 的 OS。在 Kubernetes {{< skew currentVersion >}} 中，`pod.spec.os.name` 可选的值包括
  `windows` 和 `linux`。
- `ImmutableEphemeralVolumes`：允许将各个 Secret 和 ConfigMap 标记为不可变更的，
  以提高安全性和性能。
- `IndexedJob`：允许 [Job](/zh-cn/docs/concepts/workloads/controllers/job/)
   控制器来管理每个完成索引的 Pod 完成。
- `IngressClassNamespacedParams`：允许在 `IngressClass` 资源中使用命名空间范围的参数引用。
  此功能为 `IngressClass.spec.parameters` 添加了两个字段 - `scope` 和 `namespace`。
- `Initializers`：允许使用 Intializers 准入插件来异步协调对象创建操作。
- `InTreePluginAWSUnregister`：在 kubelet 和卷控制器上关闭注册 aws-ebs 内嵌插件。
- `InTreePluginAzureDiskUnregister`：在 kubelet 和卷控制器上关闭注册 azuredisk 内嵌插件。
- `InTreePluginAzureFileUnregister`：在 kubelet 和卷控制器上关闭注册 azurefile 内嵌插件。
<!--
- `InTreePluginGCEUnregister`: Stops registering the gce-pd in-tree plugin in kubelet
  and volume controllers.
- `InTreePluginOpenStackUnregister`: Stops registering the OpenStack cinder in-tree plugin in kubelet
  and volume controllers.
- `InTreePluginPortworxUnregister`: Stops registering the Portworx in-tree plugin in kubelet
  and volume controllers.
- `InTreePluginRBDUnregister`: Stops registering the RBD in-tree plugin in kubelet
  and volume controllers.
-->
- `InTreePluginGCEUnregister`：在 kubelet 和卷控制器上关闭注册 gce-pd 内嵌插件。
- `InTreePluginOpenStackUnregister`：在 kubelet 和卷控制器上关闭注册 OpenStack cinder 内嵌插件。
- `InTreePluginPortworxUnregister`：在 kubelet 和卷控制器上关闭注册 Portworx 内嵌插件。
- `InTreePluginRBDUnregister`：在 kubelet 和卷控制器上关闭注册 RBD 内嵌插件。
<!--
- `InTreePluginvSphereUnregister`: Stops registering the vSphere in-tree plugin in kubelet
  and volume controllers.
- `IndexedJob`: Allows the [Job](/docs/concepts/workloads/controllers/job/)
  controller to manage Pod completions per completion index.
- `IngressClassNamespacedParams`: Allow namespace-scoped parameters reference in
  `IngressClass` resource. This feature adds two fields - `Scope` and `Namespace`
  to `IngressClass.spec.parameters`.
- `Initializers`: Allow asynchronous coordination of object creation using the
  Initializers admission plugin.
-->
- `InTreePluginvSphereUnregister`：在 kubelet 和卷控制器上关闭注册 vSphere 内嵌插件。
- `IndexedJob`：允许 [Job](/zh-cn/docs/concepts/workloads/controllers/job/)
  控制器根据完成索引来管理 Pod 完成。
- `IngressClassNamespacedParams`：允许在 `IngressClass` 资源中引用命名空间范围的参数。
  该特性增加了两个字段 —— `scope`、`namespace` 到 `IngressClass.spec.parameters`。
- `Initializers`： 使用 Initializers 准入插件允许异步协调对象创建。
<!--
- `JobMutableNodeSchedulingDirectives`: Allows updating node scheduling directives in
  the pod template of [Job](/docs/concepts/workloads/controllers/job).
- `JobPodFailurePolicy`: Allow users to specify handling of pod failures based on container
  exit codes and pod conditions.
- `JobReadyPods`: Enables tracking the number of Pods that have a `Ready`
  [condition](/docs/concepts/workloads/pods/pod-lifecycle/#pod-conditions).
  The count of `Ready` pods is recorded in the
  [status](/docs/reference/kubernetes-api/workload-resources/job-v1/#JobStatus)
  of a [Job](/docs/concepts/workloads/controllers/job) status.
-->
- `JobMutableNodeSchedulingDirectives`：允许在 [Job](/zh-cn/docs/concepts/workloads/controllers/job)
  的 Pod 模板中更新节点调度指令。
- `JobPodFailurePolicy`：允许用户根据容器退出码和 Pod 状况来指定 Pod 失效的处理方法。
- `JobReadyPods`：允许跟踪[状况](/zh-cn/docs/concepts/workloads/pods/pod-lifecycle/#pod-conditions)为
  `Ready` 的 Pod 的个数。`Ready` 的 Pod 记录在
  [Job](/zh-cn/docs/concepts/workloads/controllers/job) 对象的
  [status](/zh-cn/docs/reference/kubernetes-api/workload-resources/job-v1/#JobStatus) 字段中。
<!--
- `JobTrackingWithFinalizers`: Enables tracking [Job](/docs/concepts/workloads/controllers/job)
  completions without relying on Pods remaining in the cluster indefinitely.
  The Job controller uses Pod finalizers and a field in the Job status to keep
  track of the finished Pods to count towards completion.
-->
- `JobTrackingWithFinalizers`：启用跟踪 [Job](/zh-cn/docs/concepts/workloads/controllers/job)
  完成情况，而不是永远从集群剩余 Pod 来获取信息判断完成情况。Job 控制器使用
  Pod finalizers 和 Job 状态中的一个字段来跟踪已完成的 Pod 以计算完成。
<!--
- `KubeletCredentialProviders`: Enable kubelet exec credential providers for
  image pull credentials.
- `KubeletInUserNamespace`: Enables support for running kubelet in a
  {{<glossary_tooltip text="user namespace" term_id="userns">}}.
   See [Running Kubernetes Node Components as a Non-root User](/docs/tasks/administer-cluster/kubelet-in-userns/).
-->
- `KubeletCredentialProviders`：允许使用 kubelet exec 凭据提供程序来设置镜像拉取凭据。
- `KubeletInUserNamespace`：支持在{{<glossary_tooltip text="用户名字空间" term_id="userns">}}里运行 kubelet。
  请参见[使用非 Root 用户来运行 Kubernetes 节点组件](/zh-cn/docs/tasks/administer-cluster/kubelet-in-userns/)。
<!--
- `KubeletPodResources`: Enable the kubelet's pod resources gRPC endpoint. See
  [Support Device Monitoring](https://github.com/kubernetes/enhancements/blob/master/keps/sig-node/606-compute-device-assignment/README.md)
  for more details.
- `KubeletPodResourcesGetAllocatable`: Enable the kubelet's pod resources
  `GetAllocatableResources` functionality. This API augments the
  [resource allocation reporting](/docs/concepts/extend-kubernetes/compute-storage-net/device-plugins/#monitoring-device-plugin-resources)
  with informations about the allocatable resources, enabling clients to properly
  track the free compute resources on a node.
- `KubeletTracing`: Add support for distributed tracing in the kubelet.
  When enabled, kubelet CRI interface and authenticated http servers are instrumented to generate
  OpenTelemetry trace spans.
  See [Traces for Kubernetes System Components](/docs/concepts/cluster-administration/system-traces)
  for more details.
- `LegacyServiceAccountTokenNoAutoGeneration`: Stop auto-generation of Secret-based
  [service account tokens](/docs/reference/access-authn-authz/authentication/#service-account-tokens).
-->
- `KubeletPodResources`：启用 kubelet 上 Pod 资源 GRPC 端点。更多详细信息，
  请参见[支持设备监控](https://github.com/kubernetes/enhancements/blob/master/keps/sig-node/compute-device-assignment.md)。
- `KubeletPodResourcesGetAllocatable`：启用 kubelet 的 Pod 资源的 `GetAllocatableResources` 功能。
  该 API 增强了[资源分配报告](/zh-cn/docs/concepts/extend-kubernetes/compute-storage-net/device-plugins/#monitoring-device-plugin-resources)
  包含有关可分配资源的信息，使客户端能够正确跟踪节点上的可用计算资源。
- `KubeletTracing`：新增在 Kubelet 中对分布式追踪的支持。
  启用时，kubelet CRI 接口和经身份验证的 http 服务器被插桩以生成 OpenTelemetry 追踪 span。
  参阅[针对 Kubernetes 系统组件的追踪](/zh-cn/docs/concepts/cluster-administration/system-traces/)
  获取更多详细信息。
- `LegacyServiceAccountTokenNoAutoGeneration`：停止基于 Secret
  自动生成[服务账号令牌](/zh-cn/docs/reference/access-authn-authz/authentication/#service-account-tokens)。
<!--
- `LocalStorageCapacityIsolation`: Enable the consumption of
  [local ephemeral storage](/docs/concepts/configuration/manage-resources-containers/)
  and also the `sizeLimit` property of an
  [emptyDir volume](/docs/concepts/storage/volumes/#emptydir).
- `LocalStorageCapacityIsolationFSQuotaMonitoring`: When `LocalStorageCapacityIsolation`
  is enabled for
  [local ephemeral storage](/docs/concepts/configuration/manage-resources-containers/)
  and the backing filesystem for [emptyDir volumes](/docs/concepts/storage/volumes/#emptydir)
  supports project quotas and they are enabled, use project quotas to monitor
  [emptyDir volume](/docs/concepts/storage/volumes/#emptydir) storage consumption rather than
  filesystem walk for better performance and accuracy.
-->
- `LocalStorageCapacityIsolation`：允许使用
  [本地临时存储](/zh-cn/docs/concepts/configuration/manage-resources-containers/)
  以及 [emptyDir 卷](/zh-cn/docs/concepts/storage/volumes/#emptydir)的 `sizeLimit` 属性。
- `LocalStorageCapacityIsolationFSQuotaMonitoring`：如果
  [本地临时存储](/zh-cn/docs/concepts/configuration/manage-resources-containers/)启用了
  `LocalStorageCapacityIsolation`，并且
  [emptyDir 卷](/zh-cn/docs/concepts/storage/volumes/#emptydir)的后备文件系统支持项目配额，
  并且启用了这些配额，将使用项目配额来监视
  [emptyDir 卷](/zh-cn/docs/concepts/storage/volumes/#emptydir)的存储消耗而不是遍历文件系统，
  以此获得更好的性能和准确性。
<!--
- `LogarithmicScaleDown`: Enable semi-random selection of pods to evict on controller scaledown
  based on logarithmic bucketing of pod timestamps.
- `MatchLabelKeysInPodTopologySpread`: Enable the `matchLabelKeys` field for 
  [Pod topology spread constraints](/docs/concepts/scheduling-eviction/topology-spread-constraints/).
- `MaxUnavailableStatefulSet`: Enables setting the `maxUnavailable` field for the
  [rolling update strategy](/docs/concepts/workloads/controllers/statefulset/#rolling-updates)
  of a StatefulSet. The field specifies the maximum number of Pods
  that can be unavailable during the update.
- `MemoryManager`: Allows setting memory affinity for a container based on
  NUMA topology.
- `MemoryQoS`: Enable memory protection and usage throttle on pod / container using
  cgroup v2 memory controller.
- `MinDomainsInPodTopologySpread`: Enable `minDomains` in
  [Pod topology spread constraints](/docs/concepts/scheduling-eviction/topology-spread-constraints/).
- `MixedProtocolLBService`: Enable using different protocols in the same `LoadBalancer` type
  Service instance.
-->
- `LogarithmicScaleDown`：启用 Pod 的半随机（semi-random）选择，控制器将根据 Pod
  时间戳的对数桶按比例缩小去驱逐 Pod。
- `MatchLabelKeysInPodTopologySpread`：为
  [Pod 拓扑分布约束](/zh-cn/docs/concepts/scheduling-eviction/topology-spread-constraints/)启用 `matchLabelKeys` 字段。
- `MaxUnavailableStatefulSet`：启用为 StatefulSet
  的[滚动更新策略](/zh-cn/docs/concepts/workloads/controllers/statefulset/#rolling-updates)设置
  `maxUnavailable` 字段。该字段指定更新过程中不可用 Pod 个数的上限。
- `MemoryManager`：允许基于 NUMA 拓扑为容器设置内存亲和性。
- `MemoryQoS`：使用 cgroup v2 内存控制器在 Pod / 容器上启用内存保护和使用限制。
- `MinDomainsInPodTopologySpread`：在
  [Pod 拓扑分布约束](/zh-cn/docs/concepts/scheduling-eviction/topology-spread-constraints/)中启用 `minDomains`。
- `MixedProtocolLBService`：允许在同一 `LoadBalancer` 类型的 Service 实例中使用不同的协议。
<!--
- `MultiCIDRRangeAllocator`: Enables the MultiCIDR range allocator.
- `NetworkPolicyEndPort`: Enable use of the field `endPort` in NetworkPolicy objects,
  allowing the selection of a port range instead of a single port.
- `NetworkPolicyStatus`: Enable the `status` subresource for NetworkPolicy objects.
- `NodeInclusionPolicyInPodTopologySpread`: Enable using `nodeAffinityPolicy` and `nodeTaintsPolicy` in
  [Pod topology spread constraints](/docs/concepts/scheduling-eviction/topology-spread-constraints/)
  when calculating pod topology spread skew.
-->
- `MultiCIDRRangeAllocator`：启用 MultiCIDR 范围分配器。
- `NetworkPolicyEndPort`：在 NetworkPolicy 对象中启用 `endPort` 以允许选择端口范围而不是单个端口。
- `NetworkPolicyStatus`：为 NetworkPolicy 对象启用 `status` 子资源。
- `NodeInclusionPolicyInPodTopologySpread`：在计算 Pod 拓扑分布偏差时启用在
  [Pod 拓扑分布约束](/zh-cn/docs/concepts/scheduling-eviction/topology-spread-constraints/)中使用
  `nodeAffinityPolicy` and `nodeTaintsPolicy`。
<!--
- `NodeOutOfServiceVolumeDetach`: When a Node is marked out-of-service using the
  `node.kubernetes.io/out-of-service` taint, Pods on the node will be forcefully deleted
   if they can not tolerate this taint, and the volume detach operations for Pods terminating
   on the node will happen immediately. The deleted Pods can recover quickly on different nodes.
- `NodeSwap`: Enable the kubelet to allocate swap memory for Kubernetes workloads on a node.
  Must be used with `KubeletConfiguration.failSwapOn` set to false.
  For more details, please see [swap memory](/docs/concepts/architecture/nodes/#swap-memory)
- `NonPreemptingPriority`: Enable `preemptionPolicy` field for PriorityClass and Pod.
- `OpenAPIEnums`: Enables populating "enum" fields of OpenAPI schemas in the
  spec returned from the API server.
- `OpenAPIV3`: Enables the API server to publish OpenAPI v3.
-->
- `NodeOutOfServiceVolumeDetach`：当使用 `node.kubernetes.io/out-of-service`
  污点将节点标记为停止服务时，节点上不能容忍这个污点的 Pod 将被强制删除，
  并且该在节点上被终止的 Pod 将立即进行卷分离操作。
- `NodeSwap`：启用 kubelet 为节点上的 Kubernetes 工作负载分配交换内存的能力。
  必须将 `KubeletConfiguration.failSwapOn` 设置为 false 的情况下才能使用。
  更多详细信息，请参见[交换内存](/zh-cn/docs/concepts/architecture/nodes/#swap-memory)。
- `NonPreemptingPriority`：为 PriorityClass 和 Pod 启用 `preemptionPolicy` 选项。
- `OpenAPIEnums`：允许在从 API 服务器返回的 spec 中填充 OpenAPI 模式的 "enum" 字段。
- `OpenAPIV3`：允许 API 服务器发布 OpenAPI V3。
<!--
- `PodDeletionCost`: Enable the [Pod Deletion Cost](/docs/concepts/workloads/controllers/replicaset/#pod-deletion-cost)
   feature which allows users to influence ReplicaSet downscaling order.
- `PodAffinityNamespaceSelector`: Enable the
  [Pod Affinity Namespace Selector](/docs/concepts/scheduling-eviction/assign-pod-node/#namespace-selector)
  and [CrossNamespacePodAffinity](/docs/concepts/policy/resource-quotas/#cross-namespace-pod-affinity-quota)
  quota scope features.
- `PodAndContainerStatsFromCRI`: Configure the kubelet to gather container and
  pod stats from the CRI container runtime rather than gathering them from cAdvisor.
- `PodDisruptionConditions`: Enables support for appending a dedicated pod condition indicating that the pod is being deleted due to a disruption.
- `PodHasNetworkCondition`: Enable the kubelet to mark the [PodHasNetwork](/docs/concepts/workloads/pods/pod-lifecycle/#pod-has-network) condition on pods.
- `PodOverhead`: Enable the [PodOverhead](/docs/concepts/scheduling-eviction/pod-overhead/)
  feature to account for pod overheads.
-->
- `PodDeletionCost`：启用 [Pod 删除成本](/zh-cn/docs/concepts/workloads/controllers/replicaset/#pod-deletion-cost)功能。
  该功能使用户可以影响 ReplicaSet 的降序顺序。
- `PodAffinityNamespaceSelector`：启用 [Pod 亲和性名字空间选择算符](/zh-cn/docs/concepts/scheduling-eviction/assign-pod-node/#namespace-selector)和
  [CrossNamespacePodAffinity](/zh-cn/docs/concepts/policy/resource-quotas/#cross-namespace-pod-affinity-quota)
  资源配额功能。
- `PodAndContainerStatsFromCRI`：配置 kubelet 从 CRI 容器运行时中而不是从 cAdvisor 中采集容器和 Pod 统计信息。
- `PodDisruptionConditions`：启用支持追加一个专用的 Pod 状况，以表示 Pod 由于某个干扰正在被删除。
- `PodHasNetworkCondition`：使得 kubelet 能够对 Pod 标记
  [PodHasNetwork](/zh-cn/docs/concepts/workloads/pods/pod-lifecycle/#pod-has-network) 状况。
- `PodOverhead`：启用 [PodOverhead](/zh-cn/docs/concepts/scheduling-eviction/pod-overhead/)
  特性以考虑 Pod 开销。
<!--
- `PodSecurity`: Enables the `PodSecurity` admission plugin.
- `PreferNominatedNode`: This flag tells the scheduler whether the nominated
  nodes will be checked first before looping through all the other nodes in
  the cluster.
-->
- `PodSecurity`: 开启 `PodSecurity` 准入控制插件。
- `PreferNominatedNode`: 这个标志告诉调度器在循环遍历集群中的所有其他节点之前，
  是否首先检查指定的节点。
<!--
- `ProbeTerminationGracePeriod`: Enable [setting probe-level
  `terminationGracePeriodSeconds`](/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#probe-level-terminationgraceperiodseconds)
  on pods. See the [enhancement proposal](https://github.com/kubernetes/enhancements/tree/master/keps/sig-node/2238-liveness-probe-grace-period)
  for more details.
- `ProcMountType`: Enables control over the type proc mounts for containers
  by setting the `procMount` field of a SecurityContext.
- `ProxyTerminatingEndpoints`: Enable the kube-proxy to handle terminating
  endpoints when `ExternalTrafficPolicy=Local`.
- `QOSReserved`: Allows resource reservations at the QoS level preventing pods
  at lower QoS levels from bursting into resources requested at higher QoS levels
  (memory only for now).
- `ReadWriteOncePod`: Enables the usage of `ReadWriteOncePod` PersistentVolume
  access mode.
-->
- `ProbeTerminationGracePeriod`：在 Pod 上启用 
  [设置探测器级别 `terminationGracePeriodSeconds`](/zh-cn/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#probe-level-terminationgraceperiodseconds)。
  有关更多信息，请参见[改进提案](https://github.com/kubernetes/enhancements/tree/master/keps/sig-node/2238-liveness-probe-grace-period)。
- `ProcMountType`：允许容器通过设置 SecurityContext 的 `procMount` 字段来控制对
  proc 文件系统的挂载方式。
- `ProxyTerminatingEndpoints`：当 `ExternalTrafficPolicy=Local` 时，
  允许 kube-proxy 来处理终止过程中的端点。
- `QOSReserved`：允许在 QoS 级别进行资源预留，以防止处于较低 QoS 级别的 Pod
  突发进入处于较高 QoS 级别的请求资源（目前仅适用于内存）。
- `ReadWriteOncePod`: 允许使用 `ReadWriteOncePod` 访问模式的 PersistentVolume。
<!--
- `RecoverVolumeExpansionFailure`: Enables users to edit their PVCs to smaller
  sizes so as they can recover from previously issued volume expansion failures.
  See [Recovering from Failure when Expanding Volumes](/docs/concepts/storage/persistent-volumes/#recovering-from-failure-when-expanding-volumes)
  for more details.
- `RemainingItemCount`: Allow the API servers to show a count of remaining
  items in the response to a
  [chunking list request](/docs/reference/using-api/api-concepts/#retrieving-large-results-sets-in-chunks).
- `RemoveSelfLink`: Sets the `.metadata.selfLink` field to blank (empty string) for all
  objects and collections. This field has been deprecated since the Kubernetes v1.16
  release. When this feature is enabled, the `.metadata.selfLink` field remains part of
  the Kubernetes API, but is always unset.
-->
- `RecoverVolumeExpansionFailure`：允许用户编辑其 PVC 来缩小其尺寸，
  从而从之前卷扩容发生的失败中恢复。更多细节可参见
  [从卷扩容失效中恢复](/zh-cn/docs/concepts/storage/persistent-volumes/#recovering-from-failure-when-expanding-volumes)。
- `RemainingItemCount`：允许 API 服务器在
  [分块列表请求](/zh-cn/docs/reference/using-api/api-concepts/#retrieving-large-results-sets-in-chunks)
  的响应中显示剩余条目的个数。
- `RemoveSelfLink`：将所有对象和集合的 `.metadata.selfLink` 字段设置为空（空字符串）。
  该字段自 Kubernetes v1.16 版本以来已被弃用。
  启用此功能后，`.metadata.selfLink` 字段仍然是 Kubernetes API 的一部分，但始终未设置。
<!--
- `RetroactiveDefaultStorageClass`: Allow assigning StorageClass to unbound PVCs retroactively.
-->
- `RetroactiveDefaultStorageClass`：允许以追溯方式分配 StorageClass 给未绑定的 PVC。
<!--
- `RotateKubeletServerCertificate`: Enable the rotation of the server TLS certificate on the kubelet.
  See [kubelet configuration](/docs/reference/access-authn-authz/kubelet-tls-bootstrapping/#kubelet-configuration)
  for more details.
-->
- `RotateKubeletServerCertificate`：在 kubelet 上启用服务器 TLS 证书的轮换。
  更多详细信息，请参见
  [kubelet 配置](/zh-cn/docs/reference/access-authn-authz/kubelet-tls-bootstrapping/#kubelet-configuration)。
<!--
- `SELinuxMountReadWriteOncePod`: Speed up container startup by mounting volumes with the correct
  SELinux label instead of changing each file on the volumes recursively. The initial implementation
  focused on ReadWriteOncePod volumes.
- `SeccompDefault`: Enables the use of `RuntimeDefault` as the default seccomp profile
  for all workloads.
  The seccomp profile is specified in the `securityContext` of a Pod and/or a Container.
- `SELinuxMountReadWriteOncePod`: Allows kubelet to mount volumes for a Pod directly with the
  right SELinux label instead of applying the SELinux label recursively on every file on the
  volume.
-->
- `SELinuxMountReadWriteOncePod`：通过使用正确的 SELinux
  标签挂载卷而不是以递归方式更改这些卷上的每个文件来加速容器启动。最初的实现侧重 ReadWriteOncePod 卷。
- `SeccompDefault`: 允许将所有工作负载的默认  seccomp 配置文件为 `RuntimeDefault`。
  seccomp 配置在 Pod 或者容器的 `securityContext` 字段中指定。
- `SELinuxMountReadWriteOncePod`：允许 kubelet 直接用合适的 SELinux 标签为 Pod 挂载卷，
  而不是将 SELinux 标签以递归方式应用到卷上的每个文件。
<!--
- `ServerSideApply`: Enables the [Sever Side Apply (SSA)](/docs/reference/using-api/server-side-apply/)
  feature on the API Server.
- `ServerSideFieldValidation`: Enables server-side field validation. This means the validation
  of resource schema is performed at the API server side rather than the client side
  (for example, the `kubectl create` or `kubectl apply` command line).
- `ServiceInternalTrafficPolicy`: Enables the `internalTrafficPolicy` field on Services
- `ServiceLBNodePortControl`: Enables the `allocateLoadBalancerNodePorts` field on Services.
-->
- `ServerSideApply`：在 API 服务器上启用[服务器端应用（SSA）](/zh-cn/docs/reference/using-api/server-side-apply/)。
- `ServerSideFieldValidation`：启用服务器端字段验证。
  这意味着验证资源模式在 API 服务器端而不是客户端执行
  （例如，`kubectl create` 或 `kubectl apply` 命令行）。
- `ServiceInternalTrafficPolicy`：为服务启用 `internalTrafficPolicy` 字段。
- `ServiceLBNodePortControl`：为服务启用 `allocateLoadBalancerNodePorts` 字段。
<!--
- `ServiceLoadBalancerClass`: Enables the `loadBalancerClass` field on Services. See
  [Specifying class of load balancer implementation](/docs/concepts/services-networking/service/#load-balancer-class)
  for more details.
- `ServiceIPStaticSubrange`: Enables a strategy for Services ClusterIP allocations, whereby the
  ClusterIP range is subdivided. Dynamic allocated ClusterIP addresses will be allocated preferently
  from the upper range allowing users to assign static ClusterIPs from the lower range with a low
  risk of collision. See
  [Avoiding collisions](/docs/concepts/services-networking/service/#avoiding-collisions)
  for more details.
-->
- `ServiceLoadBalancerClass`: 为服务启用 `loadBalancerClass` 字段。
  有关更多信息，请参见[指定负载均衡器实现类](/zh-cn/docs/concepts/services-networking/service/#load-balancer-class)。
- `ServiceIPStaticSubrange`：启用服务 ClusterIP 分配策略，从而细分 ClusterIP 范围。
  动态分配的 ClusterIP 地址将优先从较高范围分配，以低冲突风险允许用户从较低范围分配静态 ClusterIP。
  更多详细信息请参阅[避免冲突](/zh-cn/docs/concepts/services-networking/service/#avoiding-collisions)
<!--
- `SizeMemoryBackedVolumes`: Enable kubelets to determine the size limit for
  memory-backed volumes (mainly `emptyDir` volumes).
- `StatefulSetMinReadySeconds`: Allows `minReadySeconds` to be respected by
  the StatefulSet controller.
-->
- `SizeMemoryBackedVolumes`：允许 kubelet 检查基于内存制备的卷的尺寸约束（目前主要针对 `emptyDir` 卷）。
- `StatefulSetMinReadySeconds`: 允许 StatefulSet 控制器采纳 `minReadySeconds` 设置。
<!--
- `StorageVersionAPI`: Enable the
  [storage version API](/docs/reference/generated/kubernetes-api/{{< param "version" >}}/#storageversion-v1alpha1-internal-apiserver-k8s-io).
- `StorageVersionHash`: Allow API servers to expose the storage version hash in the
  discovery.
- `SuspendJob`: Enable support to suspend and resume Jobs. For more details, see
   [the Jobs docs](/docs/concepts/workloads/controllers/job/).
-->
- `StorageVersionAPI`：
  启用[存储版本 API](/docs/reference/generated/kubernetes-api/{{< param "version" >}}/#storageversion-v1alpha1-internal-apiserver-k8s-io)。
- `StorageVersionHash`：允许 API 服务器在版本发现中公开存储版本的哈希值。
- `SuspendJob`：启用对追加和恢复 Job 的支持。更多细节请参阅
  [Job 文档](/docs/concepts/workloads/controllers/job/)。
<!--
- `TopologyAwareHints`: Enables topology aware routing based on topology hints
  in EndpointSlices. See [Topology Aware
  Hints](/docs/concepts/services-networking/topology-aware-hints/) for more
  details.
- `TopologyManager`: Enable a mechanism to coordinate fine-grained hardware resource
  assignments for different components in Kubernetes. See
  [Control Topology Management Policies on a node](/docs/tasks/administer-cluster/topology-manager/).
- `UserNamespacesStatelessPodsSupport`: Enable user namespace support for stateless Pods.
-->
- `TopologyAwareHints`： 在 EndpointSlices 中启用基于拓扑提示的拓扑感知路由。
  更多详细信息可参见[拓扑感知提示](/zh-cn/docs/concepts/services-networking/topology-aware-hints/)。
- `TopologyManager`：启用一种机制来协调 Kubernetes 不同组件的细粒度硬件资源分配。
  详见[控制节点上的拓扑管理策略](/zh-cn/docs/tasks/administer-cluster/topology-manager/)。
- `UserNamespacesStatelessPodsSupport`：为无状态 Pod 启用用户名字空间的支持。
<!--
- `VolumeCapacityPriority`: Enable support for prioritizing nodes in different
  topologies based on available PV capacity.
-->
- `VolumeCapacityPriority`: 基于可用 PV 容量的拓扑，启用对不同节点的优先级支持。
<!--
- `WatchBookmark`: Enable support for watch bookmark events.
- `WinDSR`: Allows kube-proxy to create DSR loadbalancers for Windows.
- `WinOverlay`: Allows kube-proxy to run in overlay mode for Windows.
-->
- `WatchBookmark`：启用对 watch 操作中 bookmark 事件的支持。
- `WinDSR`：允许 kube-proxy 为 Windows 创建 DSR 负载均衡。
- `WinOverlay`：允许在 Windows 的覆盖网络模式下运行 kube-proxy。
<!--
- `WindowsHostProcessContainers`: Enables support for Windows HostProcess containers.
-->
- `WindowsHostProcessContainers`：启用对 Windows HostProcess 容器的支持。

## {{% heading "whatsnext" %}}

<!--
* The [deprecation policy](/docs/reference/using-api/deprecation-policy/) for Kubernetes explains
  the project's approach to removing features and components.
* Since Kubernetes 1.24, new beta APIs are not enabled by default.  When enabling a beta
  feature, you will also need to enable any associated API resources.
  For example, to enable a particular resource like
  `storage.k8s.io/v1beta1/csistoragecapacities`, set `--runtime-config=storage.k8s.io/v1beta1/csistoragecapacities`.
  See [API Versioning](/docs/reference/using-api/#api-versioning) for more details on the command line flags.
-->
* Kubernetes 的[弃用策略](/zh-cn/docs/reference/using-api/deprecation-policy/)介绍了项目针对已移除特性和组件的处理方法。
* 从 Kubernetes 1.24 开始，默认不启用新的 Beta API。
  启用 Beta 功能时，还需要启用所有关联的 API 资源。
  例如：要启用一个特定资源，如 `storage.k8s.io/v1beta1/csistoragecapacities`，
  请设置 `--runtime-config=storage.k8s.io/v1beta1/csistoragecapacities`。
  有关命令行标志的更多详细信息，请参阅 [API 版本控制](/zh-cn/docs/reference/using-api/#api-versioning)。
