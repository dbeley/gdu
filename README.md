# gdu - Go Disk Usage

[![Build Status](https://travis-ci.com/dundee/gdu.svg?branch=master)](https://travis-ci.com/dundee/gdu)
[![codecov](https://codecov.io/gh/dundee/gdu/branch/master/graph/badge.svg)](https://codecov.io/gh/dundee/gdu)
[![Go Report Card](https://goreportcard.com/badge/github.com/dundee/gdu)](https://goreportcard.com/report/github.com/dundee/gdu)

Pretty fast disk usage analyzer written in Go.

Gdu is intended primarily for SSD disks where it can fully utilize parallel processing.
However HDDs work as well, but the performance gain is not so huge.

<img src="/assets/demo.gif" width="100%" />

## Installation

Head for the [releases](https://github.com/dundee/gdu/releases) and download binary for your system.

Using curl:

    curl -L https://github.com/dundee/gdu/releases/download/v1.6.0/gdu-linux-amd64.tgz | tar xz
    chmod +x gdu-linux-amd64
    mv gdu-linux-amd64 /usr/bin/gdu

Arch Linux:

    yay -S gdu

Brew:

    brew tap dundee/taps
    brew install gdu

Go:

    go get -u github.com/dundee/gdu


## Usage

    gdu                                 # show all mounted disks
    gdu some_dir_to_analyze             # analyze given dir
    gdu -log-file=./gdu.log some_dir    # write errors to log file
    gdu -ignore=/sys,/proc /            # ignore some paths


## Running tests

    make test


## Benchmark

Scanning 80G of data on 500 GB SSD.

Tool        | Without cache | With cache
 ---        | ---           | --- 
gdu /       | 6.5s          | 2.5s
dua /       | 8s            | 2s
godu /      | 8.5s          | 3s
du -hs /    | 44s           | 4.5s
duc index / | 47s           | 5s
ncdu /      | 54s           | 12s

Gdu is inspired by [ncdu](https://dev.yorhel.nl/ncdu), [godu](https://github.com/viktomas/godu), [dua](https://github.com/Byron/dua-cli) and [df](https://www.gnu.org/software/coreutils/manual/html_node/df-invocation.html).