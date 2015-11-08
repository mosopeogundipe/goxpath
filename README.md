# goxpath
An XPATH implementation in Go.

Currently only supports abbreviated element names.  More to come later.

###Installation
    go get github.com/ChrisTrenkamp/goxpath

###Example

#####test.xml
    <?xml version="1.0" encoding="UTF-8"?>
    <p1>
      <p2>
        <p3/>
      </p2>
      <p2>
        <p3/>
      </p2>
    </p1>

#####Absolute path
    $ goxpath '/p1' test.xml 
    <p1>
    &#x9;<p2>
    &#x9;&#x9;<p3></p3>
    &#x9;</p2>
    &#x9;<p2>
    &#x9;&#x9;<p3></p3>
    &#x9;</p2>
    </p1>
    
    $ goxpath '/p1/p2/p3' test.xml 
    <p3></p3>
    <p3></p3>

#####Relative path
    $ goxpath '//p2' test.xml 
    <p2>
    &#x9;&#x9;<p3></p3>
    &#x9;</p2>
    <p2>
    &#x9;&#x9;<p3></p3>
    &#x9;</p2>
    
    $ goxpath '//p3' test.xml 
    <p3></p3>
    <p3></p3>
