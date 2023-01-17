Kubernetes objects are persistent entities in the Kubernetes system. Kubernetes uses these entities to represent the state of your cluster. Specifically, they can describe:
-   What containerized applications are running (and on which nodes)
-   The resources available to those applications
-   The policies around how those applications behave, such as restart policies, upgrades, and fault-tolerance

[Object spec and status](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-architecture/api-conventions.md)
* Spec : The desired state of an object
* Status : The actual state of an object
[Describing a Kubernetes object](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/#describing-a-kubernetes-object) through API/yaml
-   `apiVersion` - Which version of the Kubernetes API you're using to create this object
-   `kind` - What kind of object you want to create
-   `metadata` - Data that helps uniquely identify the object, including a `name` string, `UID`, and optional `namespace`
-   `spec` - What state you desire for the object
Management Techniques of objects via API/kubectl
*  Imperative commands : Live objects - Development projects
	* eg  : kubectl create deployment nginx --image nginx
* Imperative object configuration : Individual files - Production projects
	* eg : kubectl delete -f nginx.yaml -f redis.yaml
* Declarative object configuration : Directories of files - Production projects
	* User does not define the operations to be taken on the files. Create, update, and delete operations are automatically detected per-object by `kubectl`
	* eg : 
```sh
kubectl diff -f configs/
kubectl apply -f configs/
```

* Metadata
	* Object Names and IDs 
		* Each object in your cluster has a [_Name_](https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names) that is unique for that type of resource. Every Kubernetes object also has a [_UID_](https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#uids) (Kubernetes systems-generated) that is unique across your whole cluster.
	* Labels and Selectors
		* Labels are key/value pairs that are attached to objects, such as pods. Labels are intended to be used to specify identifying attributes of objects that are meaningful and relevant to users, but do not directly imply semantics to the core system. Labels can be used to organize and to select subsets of objects. Labels can be attached to objects at creation time and subsequently added and modified at any time.
		* Selectors are used by the client/user can identify a set of objects.
			* _equality-based_ : 
				* environment = production
				* tier != frontend
				* environment=production,tier!=frontend
			* _set-based_  : 
				* environment in (production, qa)
				* tier notin (frontend, backend)
				* partition
				* !partition
			* List and Watching using kubectl/API
				* kubectl get pods -l 'environment in (production),tier in (frontend)'
	* Namespaces 
		* Mechanism for isolating groups of resources within a single cluster.Namespaces are a way to divide cluster resources between multiple users (via [resource quota](https://kubernetes.io/docs/concepts/policy/resource-quotas/)).
		* Namespaces and DNS : When you create a [Service](https://kubernetes.io/docs/concepts/services-networking/service/), it creates a corresponding [DNS entry](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/). This entry is of the form `<service-name>.<namespace-name>.svc.cluster.local`
	* Annotations
		* You can use Kubernetes annotations to attach arbitrary non-identifying metadata to objects. Clients such as tools and libraries can retrieve this metadata.The metadata in an annotation can be small or large, structured or unstructured, and can include characters not permitted by labels.
		* Example
			* Fields managed by a declarative configuration layer. Attaching these fields as annotations distinguishes them from default values set by clients or servers, and from auto-generated fields and fields set by auto-sizing or auto-scaling systems.
			* Build, release, or image information like timestamps, release IDs, git branch, PR numbers, image hashes, and registry address.
			* 
	* Field Selector
		* _Field selectors_ let you [select Kubernetes resources](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects) based on the value of one or more resource fields.
	* Finalizers
		* Finalizers are namespaced keys that tell Kubernetes to wait until specific conditions are met before it fully deletes resources marked for deletion. Finalizers alert [controllers](https://kubernetes.io/docs/concepts/architecture/controller/) to clean up resources the deleted object owned.
		* Example
			* A common example of a finalizer is `kubernetes.io/pv-protection`, which prevents accidental deletion of `PersistentVolume` objects. When a `PersistentVolume` object is in use by a Pod, Kubernetes adds the `pv-protection` finalizer. If you try to delete the `PersistentVolume`, it enters a `Terminating` status, but the controller can't delete it because the finalizer exists. When the Pod stops using the `PersistentVolume`, Kubernetes clears the `pv-protection` finalizer, and the controller deletes the volume
	* Owners and Dependents
		* In Kubernetes, some objects are _owners_ of other objects.Dependent objects also have an `ownerReferences.blockOwnerDeletion` field that takes a boolean value and controls whether specific dependents can block garbage collection from deleting their owner object. Kubernetes automatically sets this field to `true`



