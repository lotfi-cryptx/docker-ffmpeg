<!-- DO NOT EDIT THIS FILE MANUALLY -->
<!-- Please read https://github.com/linuxserver/docker-ffmpeg/blob/master/.github/CONTRIBUTING.md -->
[![linuxserver.io](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/linuxserver_medium.png)](https://linuxserver.io)

[![Blog](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=Blog)](https://blog.linuxserver.io "all the things you can do with our containers including How-To guides, opinions and much more!")
[![Discord](https://img.shields.io/discord/354974912613449730.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=Discord&logo=discord)](https://discord.gg/YWrKVTn "realtime support / chat with the community and the team.")
[![Discourse](https://img.shields.io/discourse/https/discourse.linuxserver.io/topics.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&logo=discourse)](https://discourse.linuxserver.io "post on our community forum.")
[![Fleet](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=Fleet)](https://fleet.linuxserver.io "an online web interface which displays all of our maintained images.")
[![GitHub](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=GitHub&logo=github)](https://github.com/linuxserver "view the source for all of our repositories.")
[![Open Collective](https://img.shields.io/opencollective/all/linuxserver.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=Supporters&logo=open%20collective)](https://opencollective.com/linuxserver "please consider helping us by either donating or contributing to our budget")

The [LinuxServer.io](https://linuxserver.io) team brings you another container release featuring :-

 * regular and timely application updates
 * easy user mappings (PGID, PUID)
 * custom base image with s6 overlay
 * weekly base OS updates with common layers across the entire LinuxServer.io ecosystem to minimise space usage, down time and bandwidth
 * regular security updates

Find us at:
* [Blog](https://blog.linuxserver.io) - all the things you can do with our containers including How-To guides, opinions and much more!
* [Discord](https://discord.gg/YWrKVTn) - realtime support / chat with the community and the team.
* [Discourse](https://discourse.linuxserver.io) - post on our community forum.
* [Fleet](https://fleet.linuxserver.io) - an online web interface which displays all of our maintained images.
* [Open Collective](https://opencollective.com/linuxserver) - please consider helping us by either donating or contributing to our budget

[![Scarf.io pulls](https://scarf.sh/installs-badge/linuxserver-ci/linuxserver%2Fffmpeg?color=94398d&label-color=555555&logo-color=ffffff&style=for-the-badge&package-type=docker)](https://scarf.sh/gateway/linuxserver-ci/docker/linuxserver%2Fffmpeg)
[![GitHub Stars](https://img.shields.io/github/stars/linuxserver/docker-ffmpeg.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&logo=github)](https://github.com/linuxserver/docker-ffmpeg)
[![GitHub Release](https://img.shields.io/github/release/linuxserver/docker-ffmpeg.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&logo=github)](https://github.com/linuxserver/docker-ffmpeg/releases)
[![GitHub Package Repository](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=GitHub%20Package&logo=github)](https://github.com/linuxserver/docker-ffmpeg/packages)
[![GitLab Container Registry](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=GitLab%20Registry&logo=gitlab)](https://gitlab.com/linuxserver.io/docker-ffmpeg/container_registry)
[![Quay.io](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=Quay.io)](https://quay.io/repository/linuxserver.io/ffmpeg)
[![Docker Pulls](https://img.shields.io/docker/pulls/linuxserver/ffmpeg.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=pulls&logo=docker)](https://hub.docker.com/r/linuxserver/ffmpeg)
[![Docker Stars](https://img.shields.io/docker/stars/linuxserver/ffmpeg.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=stars&logo=docker)](https://hub.docker.com/r/linuxserver/ffmpeg)
[![Jenkins Build](https://img.shields.io/jenkins/build?labelColor=555555&logoColor=ffffff&style=for-the-badge&jobUrl=https%3A%2F%2Fci.linuxserver.io%2Fjob%2FDocker-Pipeline-Builders%2Fjob%2Fdocker-ffmpeg%2Fjob%2Fmaster%2F&logo=jenkins)](https://ci.linuxserver.io/job/Docker-Pipeline-Builders/job/docker-ffmpeg/job/master/)

[FFmpeg](https://ffmpeg.org) - A complete, cross-platform solution to record, convert and stream audio and video.


[![ffmpeg](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/ffmpeg.png)](https://ffmpeg.org)

## Supported Architectures

We utilise the docker manifest for multi-platform awareness. More information is available from docker [here](https://github.com/docker/distribution/blob/master/docs/spec/manifest-v2-2.md#manifest-list) and our announcement [here](https://blog.linuxserver.io/2019/02/21/the-lsio-pipeline-project/).

Simply pulling `lscr.io/linuxserver/ffmpeg:latest` should retrieve the correct image for your arch, but you can also pull specific arch images via tags.

The architectures supported by this image are:

| Architecture | Available | Tag |
| :----: | :----: | ---- |
| x86-64 | ✅ | amd64-\<version tag\> |
| arm64 | ✅ | arm64v8-\<version tag\> |
| armhf| ❌ | arm32v7-\<version tag\> |

## Usage

Unlike most of our container library this image is meant to be run ephemerally from the command line parsing user input for a custom FFmpeg command. You will need to understand some Docker basics to use this image and be familiar with how to construct an FFmpeg command. In the commands below we will be bind mounting our current working directory from the CLI to /config, the assumption is that input.mkv is in your current working directory.

If an input file is detected we will run FFmpeg as that user/group so the output file will match its permissions.
The image supports Hardware acceleration on x86 pay close attention to the variables for the examples below.

### Included Intel Drivers (latest versions compiled):
- iHD Driver: Supports gen8+ (default for Intel)
- i965 Driver: Supports gen5+ (for gen5-gen9.5 it can be enabled by setting env var `LIBVA_DRIVER_NAME=i965` in docker arguments)
- Libva (VAAPI): Supports gen5+ with i965 driver and gen8+ with iHD driver
- Qsv Dispatcher: OneVPL (supports both OneVPL and MSDK runtimes and should automatically switch)
- Qsv Runtime:
  - OneVPL: Supports gen12+
  - MSDK (libmfx): Supports gen8 - gen12

### Basic Transcode

```
docker run --rm -it \
  -v $(pwd):/config \
  linuxserver/ffmpeg \
  -i /config/input.mkv \
  -c:v libx264 \
  -b:v 4M \
  -vf scale=1280:720 \
  -c:a copy \
  /config/output.mkv
```

### Hardware accelerated (VAAPI) ([click for more info](https://trac.ffmpeg.org/wiki/Hardware/VAAPI))

```
docker run --rm -it \
  --device=/dev/dri:/dev/dri \
  -v $(pwd):/config \
  linuxserver/ffmpeg \
  -vaapi_device /dev/dri/renderD128 \
  -i /config/input.mkv \
  -c:v h264_vaapi \
  -b:v 4M \
  -vf 'format=nv12|vaapi,hwupload,scale_vaapi=w=1280:h=720' \
  -c:a copy \
  /config/output.mkv
```

### Hardware accelerated (QSV) ([click for more info](https://trac.ffmpeg.org/wiki/Hardware/QuickSync))

```
docker run --rm -it \
  --device=/dev/dri:/dev/dri \
  -v $(pwd):/config \
  linuxserver/ffmpeg \
  -hwaccel qsv \
  -c:v h264_qsv \
  -i /config/input.mkv \
  -c:v h264_qsv \
  -global_quality 25 \
  /config/output.mkv
```

### Nvidia Hardware accelerated ([click for more info](https://trac.ffmpeg.org/wiki/HWAccelIntro#CUDANVENCNVDEC))

```
docker run --rm -it \
  --runtime=nvidia \
  -v $(pwd):/config \
  linuxserver/ffmpeg \
  -hwaccel nvdec \
  -i /config/input.mkv \
  -c:v h264_nvenc \
  -b:v 4M \
  -vf scale=1280:720 \
  -c:a copy \
  /config/output.mkv
```

## Building locally

If you want to make local modifications to these images for development purposes or just to customize the logic:
```
git clone https://github.com/linuxserver/docker-ffmpeg.git
cd docker-ffmpeg
docker build \
  --no-cache \
  --pull \
  -t linuxserver/ffmpeg:latest .
```

The ARM variants can be built on x86_64 hardware using `multiarch/qemu-user-static`
```
docker run --rm --privileged multiarch/qemu-user-static:register --reset
```

Once registered you can define the dockerfile to use with `-f Dockerfile.aarch64`.

## Versions

* **13.11.23:** - Bump FFmpeg to 6.1.
* **02.11.23:** - Remove `--enable-small` from ffmpeg build options to add back some features.
* **05.10.23:** - Add support for SVT-AV1. Update various libraries.
* **16.08.23:** - Added support for WebP formats.
* **11.08.23:** - Add optional i965 driver for gen5+ support.
* **14.06.23:** - Switch to latest iHD for Intel, add qsv support.
* **13.06.23:** - Bump to 6.0, update shared libraries, deprecate armhf, combine bin stage.
* **14.12.22:** - Rebase to Jammy, bump to 5.1.2.
* **19.06.22:** - Rebase to Focal.
* **26.08.21:** - Add support for libOpenCL.
* **01.07.21:** - Bump to 4.4.
* **17.06.20:** - Bump to 4.3.
* **16.06.20:** - Add support for libvmaf.
* **01.08.19:** - Initial release.
