  byte-spec
==============

#### A declarative DSL for reading and writing binary file formats

This library implements a small DSL that is used to describe binary
serialization formats.  It was written to support reading and writing
SuperCollider synthesizer definition files for Project Overtone, but it can be
used for many binary file formats, network packets, etc...

First you describe your binary format like this:

    (defspec basic-spec
             :a :int8
             :b :int16
             :c :int32
             :d :float32
             :e :float64
             :f :string)
    
    ;; An object to serialize
    (def foo {:a 10 :b 20 :c 40 :d 23.2 :e 23.2 :f "asddf"})
    
    ;; And serialize it to a byte array like this:
    (spec-write-bytes basic-spec foo) ;; => [...bytes...]
    
    ;; reading in a byte array with the basic-spec format works like this:
    (spec-read-bytes basic-spec bytes)

There is also support for arrays of the basic types and arrays of nested spec
types.  Take a look at the tests for some more examples, and of course browsing
the source is always a good idea.  Not a lot of work has gone into making this
especially general purpose beyond what we've needed for Overtone, but if people
are interested in using it I'm happy to make it more useful for other projects
as well.

For a more full example of usage checkout overtone.core.synthdef in the project
Overtone source.  Feel free to email me with questions, comments, or patches.

### Project Info:

Include in your project.clj like so:

  [overtone/byte-spec "0.1"]

#### Source Repository
Downloads and the source repository can be found on GitHub:

  http://github.com/rosejn/byte-spec

Eventually there will be more documentation for this library, but in the
meantime you can see it in use within the context of Project Overtone, located
here:

  http://github.com/rosejn/overtone

#### Mailing List

For any questions, comments or patches, use the Overtone google group here:

http://groups.google.com/group/overtone

### Authors

* Jeff Rose
