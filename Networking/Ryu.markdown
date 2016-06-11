# Ryu
### Resources
[Ryu Using OpenFlow 1.3](https://osrg.github.io/ryu-book/en/Ryubook.pdf) is a free book that works through a number of examples.

[Ryu application API](http://ryu.readthedocs.io/en/latest/ryu_app_api.html)

[OpenFlow protocol API reference.](http://ryu.readthedocs.io/en/latest/ofproto_ref.html#ofproto-ref)  Of particular interest are the following two classes:
* [flow match structure (OFPMatch)](http://ryu.readthedocs.io/en/latest/ofproto_v1_0_ref.html#flow-match-structure) defines the fields against which an ingress packet is matched.
* [action structures (OFPAction)](http://ryu.readthedocs.io/en/latest/ofproto_v1_0_ref.html#action-structures) defines that actions that may be taken upon a match.

[Packet library](http://ryu.readthedocs.io/en/latest/library_packet.html) is used for parsing and building packets of various protocols.  This section has examples of both.

### Example
Here is how ryu is invoked:
``ryu/bin/ryu-manager simple_switch.py --verbose``

### Source Code
<https://github.com/osrg/ryu>
[examples](https://github.com/osrg/ryu/tree/master/ryu/app)

