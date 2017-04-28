<!--

********************************************************************************

WARNING:

    DO NOT EDIT "znc/README.md"

    IT IS AUTO-GENERATED

    (from the other files in "znc/" combined with a set of templates)

********************************************************************************

-->

# Supported tags and respective `Dockerfile` links

-	[`1.6.5`, `1.6`, `latest` (*full/Dockerfile*)](https://github.com/znc/znc-docker/blob/3a25a4a6ac50b4d969449696708aae2a2d8aeb22/full/Dockerfile)
-	[`1.6.5-slim`, `1.6-slim`, `slim` (*slim/Dockerfile*)](https://github.com/znc/znc-docker/blob/3a25a4a6ac50b4d969449696708aae2a2d8aeb22/slim/Dockerfile)

# Quick reference

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack/), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

-	**Where to file issues**:  
	[https://github.com/znc/znc-docker/issues](https://github.com/znc/znc-docker/issues)

-	**Maintained by**:  
	[the ZNC Community](https://github.com/znc/znc-docker)

-	**Published image artifact details**:  
	[repo-info repo's `repos/znc/` directory](https://github.com/docker-library/repo-info/blob/master/repos/znc) ([history](https://github.com/docker-library/repo-info/commits/master/repos/znc))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images PRs with label `library/znc`](https://github.com/docker-library/official-images/pulls?q=label%3Alibrary%2Fznc)  
	[official-images repo's `library/znc` file](https://github.com/docker-library/official-images/blob/master/library/znc) ([history](https://github.com/docker-library/official-images/commits/master/library/znc))

-	**Source of this description**:  
	[docs repo's `znc/` directory](https://github.com/docker-library/docs/tree/master/znc) ([history](https://github.com/docker-library/docs/commits/master/znc))

-	**Supported Docker versions**:  
	[the latest release](https://github.com/docker/docker/releases/latest) (down to 1.6 on a best-effort basis)

# What is ZNC?

ZNC is an IRC network bouncer (BNC). It can detach the client from the actual IRC server, and also from selected channels. Multiple clients from different locations can connect to a single ZNC account simultaneously and therefore appear under the same nickname on IRC.

[ZNC Wiki](http://znc.in/)

# How to use this image

ZNC in this image stores its configuration in `/znc-data`. If you have existing configuration, you can reuse it with `-v $HOME/.znc:/znc-data`. Alternatively, you can create a new config in a volume or in a local dir. The examples below assumes a volume named `znc-cfg`.

```console
$ docker run -it -v znc-cfg:/znc-data znc --makeconf
```

To run ZNC:

```console
$ docker run -p 6697:6697 -v znc-cfg:/znc-data znc
```

The port should match the port you used during `--makeconf`. Note that 6667 is often blocked by web browsers, and therefore is not recommended.

If you use any external module, put the .cpp, .py or .pm file to `/znc-data/modules` (you may need to create that directory).

Musl silently doesn't support `AI_ADDRCONFIG` yet, and ZNC doesn't support [Happy Eyeballs](https://en.wikipedia.org/wiki/Happy_Eyeballs) yet. Together they cause very slow connection. So for now IPv6 is disabled here.

# Image Variants

The `znc` images come in many flavors, each designed for a specific use case.

## `znc:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of.

## `znc:slim`

This image is smaller, but it doesn't support external modules. If you need any external C++, Perl or Python module, use `latest` instead of `slim`.

# License

View [license](https://github.com/znc/znc/blob/master/LICENSE) [information](https://github.com/znc/znc/blob/master/NOTICE) for the software contained in this image.