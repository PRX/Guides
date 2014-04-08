---
layout: post
title:  "Working with Broadcast MP2 Files"
date:   2014-04-08 13:34:44
categories: broadcast radio
---

Producing content for radio broadcast can be a great way to reach new listeners. Radio stations use computer systems to manage their programming, and nearly all of those systems expect your audio files to be formatted correctly. This guide will help you get familiar with the MP2 file format that radio stations will use to broadcast your stories, and how it fits into your production workflow.

## Source Material

Radio stations will expect the audio quality of your files to be on par with the other shows they broadcast. You are probably familiar with WAV files. Once you start producing for broadcast, you should make every effort to use high quality WAV files throughout your production process. Even if your recording equipment allows you to record straight to MP3 or some other format to save disk space, opt for the highest quality format offered.

While WAV is the most common format for recording, there are other formats in the same family, such as AIFF and PCM, that are also perfectly acceptable to use.

Because radio stations are designed for files with a sample rate of 44.1 kHz, you should record your audio at that sample rate whenever possible, even if your equipment can record at 48 or 96 kHz.

Station programmers will be able to notice when recordings are made with compressed or altered audio, and that could determine whether your work gets air time or is passed over.

#### Lossless File Formats

Even though lossless formats like FLAC and ALAC have become more common, the equipment used in radio stations generally isn't designed to handle those files. You can use those formats during production without any fear of losing quality, but you will still need to produce an MP2 file for the stations.

## What is MP2?

MP2 and the more popular MP3 share a number of historical and technological traits, but MP2 is mostly unknown to those outside of radio and certain video production industries. For many audio producers, radio broadcast is their first experience with the format.

Similar to formats you're more familiar with, like MP3 and AAC, files encoded to MP2 are designed to reduce file sizes while maintaining a reasonable level of fidelity. Whereas an MP3 file is generally about one tenth the size of the WAV file it was created from, an MP2 made from that same file will usually be closer to half the size.

### Encoding Options

The technology behind MP2 supports a wide variety of format options, such as sample rates, bit rates, and the number of channels. There is no single standard used by the broadcast equipment in radio stations, but there are some best practices you can follow to avoid any issues when trying to get your audio on the air.

#### Mono versus Stereo

Most audio productions will benefit from having two separate channels of sound. Nearly all broadcast-ready MP2s are stereo files. One supported feature of the MP2 format is a format called **intensity encoded joint stereo**. This format allows for two distinct channels of sound like standard stereo, but saves disk space by looking for similarities between the two channels during the encoding process.

If you prefer, creating a single channel, mono MP2 is also safe, even if you are mixing down multiple channels from your source materials. You could also create a stereo (or joint stereo) MP2 from a mono source file without any risk of incompatibility.

#### Sample Rate

Without exception, the sample rate of your MP2 files intended for radio should be 44100 Hz (44.1 kHz).

#### Bit Rate

In nearly all situations MP2 files for broadcast should be encoded at 128 kbps (kilobits per second) **per channel**. That means if you decide to create a mono MP2, it will be 128 kbps in total. But if you create a stereo (or joint stereo) MP2, the resulting file will be 256 kbps (128 kbps for each channel) in total. Files encoded below this rate are generally considered unfit for broadcast.

## Creating Broadcast-Ready MP2s

Once you've finished production on your audio, you're ready to create the MP2 stations can use to broadcast your work. Most popular DAWs and editing software, including Adobe Audition and Audacity, come with the ability to export or save MP2s of your project.

The specific process will depend on the software you use. If you don't have the option to control all the options that were discussed in this guide, you should consider exporting a WAV from your software and creating the MP2 with a third-party tool.

#### Encoders

PRX provides stand-alone encoder software for both Mac and Windows, which creates MP2s according the guidelines detailed in this guide. There are a number of other tools available that provide greater control over the encoding process, but are not designed specifically for radio broadcast.

## Distribution

Once the MP2 is ready, you're ready to submit your work to the various radio distributions systems. In some cases, the MP2 will be used as a mezzanine file for creating other formats, such as those used for podcasts or auditioning.
