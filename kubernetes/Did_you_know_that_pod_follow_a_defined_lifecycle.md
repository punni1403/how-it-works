𝑫𝒊𝒅 𝒚𝒐𝒖 𝒌𝒏𝒐𝒘 𝒕𝒉𝒂𝒕 𝒑𝒐𝒅𝒔 𝒇𝒐𝒍𝒍𝒐𝒘 𝒂 𝒅𝒆𝒇𝒊𝒏𝒆𝒅 𝒍𝒊𝒇𝒆𝒄𝒚𝒄𝒍𝒆? 🤔 ♻ 

They start in the 'Pending' phase, move through 'Running' if at least one of its primary containers starts OK, and then through either the 'Succeeded' or 'Failed' phases depending on whether any container in the Pod terminated in failure. 

Let's break down the phases: 
😕 𝑷𝒆𝒏𝒅𝒊𝒏𝒈: Pod has been accepted in a hashtag#Kuberenetes cluster, but one or more hashtag#containers have not been set up (scheduling issue, image issue, etc) and is not in ready state to accept traffic
✅ 𝑹𝒖𝒏𝒏𝒊𝒏𝒈: Pod has been bound to a node, and all of the containers have been created. At least one container is still running, or is in the process of starting or restarting.
✔ 𝑺𝒖𝒄𝒄𝒆𝒆𝒅𝒆𝒅: All containers in the Pod have terminated in success, and will not be restarted.
❗𝑭𝒂𝒊𝒍𝒆𝒅: All containers in the Pod have terminated, and at least one container has terminated in failure. That is, the container either exited with non-zero status or was terminated by the system.
⁉ 𝑼𝒏𝒌𝒏𝒐𝒘𝒏: The state of the Pod could not be obtained and it occurs due to an error in communicating with the node where the Pod should be running.

Tracking the phases between pod communication is important as it helps to hashtag#debug application failures quickly before looking into the core configuration!


![𝑫𝒊𝒅 𝒚𝒐𝒖 𝒌𝒏𝒐𝒘 𝒕𝒉𝒂𝒕 𝒑𝒐𝒅𝒔 𝒇𝒐𝒍𝒍𝒐𝒘 𝒂 𝒅𝒆𝒇𝒊𝒏𝒆𝒅 𝒍𝒊𝒇𝒆𝒄𝒚𝒄𝒍𝒆?](Did_you_know_that_pod_follow_a_defined_lifecycle.jpg "𝒑𝒐𝒅𝒔 𝒇𝒐𝒍𝒍𝒐𝒘 𝒂 𝒅𝒆𝒇𝒊𝒏𝒆𝒅 𝒍𝒊𝒇𝒆𝒄𝒚𝒄𝒍𝒆")
