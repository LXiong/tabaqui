#Tabaqui#

An HTTP interface to serve files/directories from HDFS. This is a temprorary project. I suggest looking at HttpFs for a more robust solution. A couple of reasons why we're using this instead:

* Read-Only access - This doesn't even support other operations
* File Merging - If you give it a path to a directory it will merge all files within that directory and write it to the response

### Version Compatability ###
This code is built with the following assumptions.  You may get mixed results if you deviate from these versions.

* [Hadoop](http://hadoop.apache.org) 0.20.2+

### Prerequisites ###

* Hadoop

### Building ###
To make a jar you can do:  

`mvn package`

The jar file is then located under `target`.

### Running an instance ###

In order to run tabaqui on another machine you will probably want to use the _dist_ assembly like so:

`mvn assembly:assembly`

The zip file now under the `target` directory should be deployed to `TABAQUI_HOME` on the remote server.

To run Tabaqui you can use `bin/tabaqui`. Here is an example of using the regular tabaqui script:

`bin/tabaqui 8080`

### REST Request Format ###

#####URI _/path_#####

GET
* The _path_ is considered to be an HDFS path. All of its file contents will be read and returned in a single response as text/plain.

Here's the list of HTTP response codes that Tabaqui could send back:

* 200 OK - A file/directory was found and written to the response.

### License ###
All aspects of this software are distributed under Apache Software License 2.0. See LICENSE file for full license text.

### Contributors ###

* Xavier Stevens ([@xstevens](http://twitter.com/xstevens))