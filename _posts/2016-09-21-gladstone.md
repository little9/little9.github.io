---
layout: post
title:  Gladstone\: A node.js based BagIt utility
author: Jamie Little
---

<a href="https://github.com/little9/gladstone">Gladstone</a> is a node.js command line utility and library
that I wrote for creating <a href="https://en.wikipedia.org/wiki/BagIt">BagIt archives</a>.

BagIt archives are standard for storing and transferring content. There are widely-deployed open source
utilities written for the standard in <a href="https://github.com/LibraryOfCongress/bagit-python">Python</a>, <a href="https://github.com/little9/bagit">Ruby</a>, and <a href="https://github.com/LibraryOfCongress/bagit-java">Java</a>. The Java and Python libraries are maintained
by the Library of Congress, which is a big user of the BagIt standard.

In its current implementation Gladstone bags whole directories recursively and then moves the resulting
bag to another destination. The Python implementation of BagIt does what's called "bag in place" style
bagging. It will create the bag in the folder you give it. This may not be what you want if you don't
want the folder you are creating your bag from to be a bag itself.

Gladstone is simpler than the other utilities, but I hope that may end up being helpful for someone
who needs to do bagging in JavaScript.

To use the command line utility you'll need to install the node module globally:

<pre>
<code class="bash">
nam install -g gladstone
</code>
</pre>

Then you can use the CLI interface:

<pre> 
<code class="bash">
gladstone --bagName ~/bagname --originDirectory ~/source --cryptoMethod md5 
</code>
</pre>

If you want to use it as a library you can require it in your node.js app:

<pre>
<code class="javascript">
var gladstone = require('gladstone');

gladstone.createBagDirectory({ bagName: '/path/to/new/bag',
                               originDirectory: '/path/to/dir/to/bag',
                               cryptoMethod: 'sha256',
                               sourceOrganization: 'Example Organization',
                               organizationAddress: '123 Street',
                               contactName: 'Contact Name',
                               contactPhone: '555-555-5555',
                               contactEmail: 'test@example.org',
                               externalDescription: 'An example description'
                            });
</code>
</pre>




