# nso-5-day-training


This training was prepared by Cisco IT Network Engineers for other network engineers. It requires no background in NSO, YANG, Python or anything else.

You will need a working copy of NSO to play around with, the examples assumed using NSO 4.4. For some of the service template examples, you may need to use the same version of the cisco-ios NED ( version 5.2.7) to get the XML to look the same.

The backbone of the content is in the [Lecture Notes PDF File](/LectureNotes). All of the labs are based off of the content given in the lectures.

This course includes:
- Automation Culture slides (some taken from Kirk Byers NANOG, with credit)
- Beginning / intermediate Yang
- NSO + Python Maagic API
- XML(taken from W3Schools mostly with credit) REST API usage
- building a package without config
- building a service package
- intermediate service templates
- All with Enterprise relevant examples (QoS, ACLs, NTP servers, etc).

Template tag operations
Templates allow for defining different behaviour when applying the template. This is accomplished by setting tags, as an attribute. Existing tags are: merge, replace, delete, create or nocreate on relevant nodes in the template. A tag in inherited to its sub-nodes until a new tag is introduced.

merge: Merge with a node if it exists, otherwise create the node. This is the default operation if no operation is explicitly set.

...
<config tags="merge">
  <interface xmlns="urn:ios">
...
 

replace: Replace a node if it exists, otherwise create the node.

...
<GigabitEthernet tags="replace">
  <name>{link/interface-number}</name>
  <description tags="merge">Link to PE</description>
...
 

create: Creates a node. The node can not already exist. An error is raised if the node exists.

...
<GigabitEthernet tags="create">
  <name>{link/interface-number}</name>
  <description tags="merge">Link to PE</description>
...
 

nocreate: Merge with a node if it exists. If it does not exist, it will not be created.

...
<GigabitEthernet tags="nocreate">
  <name>{link/interface-number}</name>
  <description tags="merge">Link to PE</description>
...
 

delete: Delete the node.

...
<GigabitEthernet tags="delete">
  <name>{link/interface-number}</name>
  <description tags="merge">Link to PE</description>
...
