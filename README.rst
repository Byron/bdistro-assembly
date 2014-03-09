This is the distribution assembly of the sister assembly called 'bdevel'. It allows libraries to exist in multiple versions at the same time, and will only contain binaries relevant to the end-user.

It is made to support various platforms at once, and will thus suit the needs of a client using multiple platforms in-house.

BDistro Assembly Structure
==========================

* lib/<library>

 + All libraries are presented in multiple versions, which allows binaries to be configured according to their actual requirements. This allows different binaries to use different versions of the same library for example.
 + The shipped libraries should just comprised of first-party content, as third-party dependencies are member of another assembly.
 + Each library is structured as follows

  - <library>/<version>/<platform>

 + <library>

  - The name of the library ,like 'alembic'

+ <version>

 - Any version identifier, which is preferably compatible to the `semantic version specification <http://semver.org>`_
  
+ <platform>
 
 - The platform for which the binaries where made, like 'centos-6_x86-64' or 'mac-os-10'. The latter only exists in 64 bit versions, which is why the architecture bits are omitted.
 - Architecture independent binaries will use the special 'noarch' platform.
  
* doc/*

 + Similar to the respective folder in the `bdevel assembly <https://github.com/Byron/bdevel-assembly>`_

* etc/*
  
  + Contains various configuration which is shared among all provided binaries