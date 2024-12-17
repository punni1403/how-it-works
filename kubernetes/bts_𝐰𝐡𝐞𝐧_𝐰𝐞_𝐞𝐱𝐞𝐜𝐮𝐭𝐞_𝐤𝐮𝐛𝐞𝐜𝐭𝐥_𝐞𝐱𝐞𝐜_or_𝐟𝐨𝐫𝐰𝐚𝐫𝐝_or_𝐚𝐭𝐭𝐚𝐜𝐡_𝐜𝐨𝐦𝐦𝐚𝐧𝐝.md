𝐰𝐡𝐚𝐭 𝐡𝐚𝐩𝐩𝐞𝐧𝐬 𝐛𝐞𝐡𝐢𝐧𝐝 𝐭𝐡𝐞 𝐬𝐜𝐞𝐧𝐞 𝐰𝐡𝐞𝐧 𝐰𝐞 𝐞𝐱𝐞𝐜𝐮𝐭𝐞 -> 𝐤𝐮𝐛𝐞𝐜𝐭𝐥 𝐞𝐱𝐞𝐜/𝐟𝐨𝐫𝐰𝐚𝐫𝐝/𝐚𝐭𝐭𝐚𝐜𝐡 𝐜𝐨𝐦𝐦𝐚𝐧𝐝.


Kubernetes Container Runtime Interface (CRI) acts as the main connection between the kubelet and the Container Runtime. Those runtimes have to provide a gRPC server which has to fulfill a Kubernetes defined Protocol Buffer interface.


Let's understand the workflow:

👉 When 'kubectl exec' is executed on a pod, the request is first handed over to the kubernetes API Server and then the API Server calls the 'kubelet Exec API'

👉 The implementation of Streaming API in CRI shim relies on a set of independent Streaming Server mechanisms

👉 At this time, kubelet calls k8s CRI’s Exec interface and the one responsible for responding to this interface is naturally the specific CRI shim

👉 Here CRI shim will not directly call any container runtime (CRI-O, containerd, rkt, etc) for processing, but only returns a URL to the kubelet

👉 Clients like crictl or the kubelet (via kubectl) request a new exec, attach or port forward session from the runtime using the gRPC interface.

👉 The runtime implements a streaming server that also manages the active sessions

👉 After the kubelet gets this URL, it returns it to the API Server in the form of 'Redirect'

👉 Now, API Server initiates a real '/exec' request to Streaming Server through redirection and establish a long connection with it !!


Ref:- https://kubernetes.io/blog/2024/05/01/cri-streaming-explained/ 

![𝐰𝐡𝐚𝐭 𝐡𝐚𝐩𝐩𝐞𝐧𝐬 𝐛𝐞𝐡𝐢𝐧𝐝 𝐭𝐡𝐞 𝐬𝐜𝐞𝐧𝐞 𝐰𝐡𝐞𝐧 𝐰𝐞 𝐞𝐱𝐞𝐜𝐮𝐭𝐞 -> 𝐤𝐮𝐛𝐞𝐜𝐭𝐥 𝐞𝐱𝐞𝐜/𝐟𝐨𝐫𝐰𝐚𝐫𝐝/𝐚𝐭𝐭𝐚𝐜𝐡 𝐜𝐨𝐦𝐦𝐚𝐧𝐝.
](bts_𝐰𝐡𝐞𝐧_𝐰𝐞_𝐞𝐱𝐞𝐜𝐮𝐭𝐞_𝐤𝐮𝐛𝐞𝐜𝐭𝐥_𝐞𝐱𝐞𝐜_or_𝐟𝐨𝐫𝐰𝐚𝐫𝐝_or_𝐚𝐭𝐭𝐚𝐜𝐡_𝐜𝐨𝐦𝐦𝐚𝐧𝐝.jpg "𝐰𝐡𝐚𝐭 𝐡𝐚𝐩𝐩𝐞𝐧𝐬 𝐛𝐞𝐡𝐢𝐧𝐝 𝐭𝐡𝐞 𝐬𝐜𝐞𝐧𝐞 𝐰𝐡𝐞𝐧 𝐰𝐞 𝐞𝐱𝐞𝐜𝐮𝐭𝐞 -> 𝐤𝐮𝐛𝐞𝐜𝐭𝐥 𝐞𝐱𝐞𝐜/𝐟𝐨𝐫𝐰𝐚𝐫𝐝/𝐚𝐭𝐭𝐚𝐜𝐡 𝐜𝐨𝐦𝐦𝐚𝐧𝐝.
")

