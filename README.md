# yacfiles

I'm using this repo to reproduce some of the bugs encountered in the wild or the opencloud CI. It is organized as follows:

```
❯ tree
.
├── env                                # constains environments that can be mixed
│   ├── host.cloud.opencloud.test.env    # my local test domain
│   ├── host.opencloud-server.env        # used by some of the test scripts
│   ├── user.admin.env                   # use user admin with password admin
│   └── user.bob.env                     # use bob with password 123 as created by the `users/create bob.http`
├── issues                             # the actual http files to reproduce issues in other repos
│   ├── 275.http
│   └── 281.http
│   └── ocis-8804.http
├── README.md
├── scratch                            # just random snippets
│   ├── audio.http
│   ├── list drives.http
│   ├── propfind.http
│   └── restore trash child.http
└── users                              # used to create users
    └── create bob.http
```

# Contributing

Happy to add files that reproduce more tests.

# TODO
## IntelliJ compatability
The tests are currently httpyac specific, but it supports IntelliJ IDE like tests as well. Would be great to remain compatible.
In the ocis-8804.http:
```
{{
  uploadlocation1 = response.headers.location;
}}
```

would become
```
> {%
  client.global.set("uploadlocation1", response.headers.location);
  uploadlocation1 = response.headers.location;
%}
```
