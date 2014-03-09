This is the distribution assembly of the sister assembly called [bdevel](https://github.com/Byron/bdevel-assembly). It allows libraries to exist in multiple versions at the same time, and will only contain binaries relevant to the end-user.

It is made to support various platforms at once, and will thus suit the needs of a client using multiple platforms in-house.

### BDistro Assembly Structure

As a general rule of thumb, path portions which are not required should just be omitted. Changes at a later time are embraced and not considered a problem.

- **lib/${library}**
    - All libraries are presented in multiple versions, which allows binaries to be configured according to their actual requirements. This allows different binaries to use different versions of the same library for example.
    - The shipped libraries should just comprised of first-party content, as unmodified third-party dependencies are member of another assembly. This implies that modified third-party content may be placed here.
    - Each library is structured as follows
        + ${library}/${version}/${platform}

    - ${library}
        + The name of the library ,like 'alembic'

    - ${version}
        + Any version identifier, which is preferably compatible to the `semantic version specification <http://semver.org>`_
  
    - ${platform} (optional)
        + The platform for which the binaries where made, like 'centos-6_x86-64' or 'mac-os-10'. The latter only exists in 64 bit versions, which is why the architecture bits are omitted.
    
    - Architecture independent binaries will use the special 'noarch' platform, which can be omitted for brevity.
  
- **doc/***
    - Similar to the respective folder in the `bdevel assembly <https://github.com/Byron/bdevel-assembly>`_

- **etc/***
    - Contains various configuration which is shared among all provided binaries