---
layout: post
title: ssh, scp, wget
modified:
categories: notes
excerpt: using ssh to connect to a server and scp wget for copying files
tags: []
image:
  feature:
date: 2016-05-20T14:26:27-04:00
---

The first UNIX commands I learned were ssh, scp and wget.  ssh is used to connect to a server, while scp and wget are used for downloading and copying files.

# ssh

## Connecting and Disconnecting to the Server

To connect to a server, type: `ssh user@server`

where user is your username and server is the name of the server

You will be prompted to enter a password. The cursor does not move/show what you are typing as you enter the password.

To disconnect from the server, you can type `exit` or hit `ctrl-D`.

## Networking

An IP address is made up of 4 bytes (32 bits).
For example: 127.0.0.1
These addresses can also be associated with names like teamerlich.org.

When you use ssh, the server can be specified either by a name or an IP address.

## Private/Public Key

Private/Public keys can be used for ssh passwordless login.

`ssh-keygen` generates two files: id-rsa (private) and id-rsa.pub (public). The private key is kept on the computer while the public key can be shared with others for secure login without a password.


# scp and wget

## Copy a local file to server
[1KGP VCF Download](ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/release/20130502/)

Download the chr 22 vcf file locally.

To copy the file to the server (run from downloads folder):

	scp ALL.chr22.phase3_shapeit2_mvncall_integrated_v5a.20130502.genotypes.vcf.gz maya@maya.teamerlich.org:~

## Download a file directly to server
ssh to server:

	ssh maya@maya.teamerlich.org

download file:

	wget ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/release/20130502/ALL.chr21.phase3_shapeit2_mvncall_integrated_v5a.20130502.genotypes.vcf.gz

## Download file from server to local computer
To copy from the server (run from where you want the file saved to):

	scp maya@maya.teamerlich.org:~/ALL.chr21.phase3_shapeit2_mvncall_integrated_v5a.20130502.genotypes.vcf.gz chr21.vcf.gz

File is saved in downloads folder with filename chr21.vcf.gz

## Copy a directory to server
Created a new directory on mac called test1. test1 contains hello.txt and world.txt.

Copy to server:

	scp -r test1 maya@maya.teamerlich.org:~

The `-r` option copies directories along with everything in them.

## Use wget to download continuously

The `-c` option can be used to continue downloading a large file after the connection/download has been interrupted (as opposed to starting the download again).