𝐊𝐮𝐛𝐞𝐫𝐧𝐞𝐭𝐞𝐬 𝐒𝐜𝐡𝐞𝐝𝐮𝐥𝐢𝐧𝐠 - 𝐀 𝐛𝐫𝐞𝐚𝐤𝐝𝐨𝐰𝐧 𝐨𝐟 𝐭𝐡𝐞 𝐢𝐧𝐭𝐞𝐫𝐧𝐚𝐥 𝐦𝐞𝐜𝐡𝐚𝐧𝐢𝐬𝐦 🤔 ☸️ 

Kubernetes scheduling is composed of two main phases:
➡️ 𝑭𝒊𝒍𝒕𝒆𝒓𝒊𝒏𝒈 : Here hashtag#Kubernetes eliminates nodes that are not suitable for running a pod
➡️ 𝑺𝒄𝒐𝒓𝒊𝒏𝒈: Kubernetes assigns a score to each remaining node based on various criteria, such as resource utilization, pod affinity, and node affinity. The node with the highest score is selected as the best fit for the pod.

Filtering & Scoring phases are implemented by two types of components
 📌𝑷𝒓𝒆𝒅𝒊𝒄𝒂𝒕𝒆𝒔: Boolean functions that return true or false for each node, implements filtering logic
📌𝑷𝒓𝒊𝒐𝒓𝒊𝒕𝒊𝒆𝒔: Numeric functions that implements a 'scoring logic' providing a score ( b/w 0 & 10) to any particular node

The scheduling algorithm to determine the appropriate worker-node kicks in based on the above factors, covering most of the key use cases as:
✅ PodFitsResources: checks if a node has enough CPU and memory to run a pod
✅ PodFitsHost: checks if a pod has a specific hostname requirement
✅ PodFitsHostPorts: checks if a node has free ports for a pod’s host port mappings
✅ PodSelectorMatches: checks if a pod’s node selector matches a node’s labels
✅ NoDiskConflict: checks if a pod’s volume mounts conflict with any other pod’s volume mounts on the same node
✅ LeastRequestedPriority: favors nodes with lower resource utilization
✅ InterPodAffinityPriority: favors nodes that match a pod’s inter-pod affinity and anti-affinity preferences
✅ TaintTolerationPriority: favors nodes that have taints that are tolerated by a pod

Refer:- https://lnkd.in/givcU-W8
