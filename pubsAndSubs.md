# Publishers and Subscribers

_If a tree falls in a forest and no one is around, does it even make a sound?_

## Concepts

- Topics
- Publishers
- Subscribers
- Messages
- How to make a message

## Topics

Read more on [ROSWiki](https://wiki.ros.org/ROS/Tutorials/UnderstandingTopics)

Topics are named buses that Nodes use to publish information (camera data, movement instructions). Topics can have a variety of data types, which depends on the message that they are sending. Think of messages as the data, the Topic like the bus, and the [Master](https://wiki.ros.org/Master) like the bus map maker who tells the buses the stops they need to go to.

Topics will only go to nodes that have "opened the bus stop", this is called subscribing to a topic. The nodes will talk directly to eachother using the Topics, and won't transmit messages through the Master, the Master just points them to the right direction. (This is like video calling, both devices need to go to a server that tells them how to format their connections and how to find eachother in the Internet, but then the two devices communicate directly with eachother after that initial locating process.)

Topics use TCP protocol to send messages by default, you can use UCP with some extra configuration, but you'd only really need this for remote or telecontrolling.

## Messages

Now we know about the bus, the messages are the people on the bus. A bus has a specific number, and you know that getting on the bus. The messages likewise are only ever in a topic that's relevant to the publisher that put them on the bus, or in the topic. All nodes along the route get the same passengers, which doesn't really fit the bus anaolgy.

Messages have headers that contain informations and fields, a standard one from ROS wiki:
```# Standard metadata for higher-level stamped data types.
# This is generally used to communicate timestamped data 
# in a particular coordinate frame.
# 
# sequence ID: consecutively increasing ID 
uint32 seq
#Two-integer timestamp that is expressed as:
# * stamp.sec: seconds (stamp_secs) since epoch (in Python the variable is called 'secs')
# * stamp.nsec: nanoseconds since stamp_secs (in Python the variable is called 'nsecs')
# time-handling sugar is provided by the client library
time stamp
#Frame this data is associated with
# 0: no frame
# 1: global frame
string frame_id ```

