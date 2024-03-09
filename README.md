# Podcast Feed Generator for iTunes

A GitHub action to generate a iTunes podcast feed a YAML file. YAML is much easier to read and write than XML, and this action will convert your YAML file into a valid podcast feed.

## Usage

### Turn on GitHub Pages

In your repository, go to Settings > Pages and select the main branch as the resource. This will create a link to ypur page and give all of the content in the main branch a URL. Note the URL for the next step.

### Create a YAML file

Create a YAML file in your repository the following format:

```yaml
title: <Podcast Title>
subtitle: <Podcast Subtitle>
author: <Author Name>
description: <Podcast Description>
link: <GitHub Pages URL>
image: <Artwork Location>
language: <Podcast Language e.g. en-us>
category: <Podcast Category e.g. Technology>
format: <Format of Files e.g. audio/mpeg>
item:
  - title: <Podcast Episode Title>
    description: <Podcast Episode Description>
    published: <Date Published e.g. Sat, 10 Mar 2024 23:35:00 GMT>
    file: <File Name e.g. /audio/TFIT01.mp3>
    duration: <Duration e.g. 00:00:36>
    length: <Length e.g. 576,324 (Get Info on your File)>
    ... Repead for each episodes
```

### Sample Workflow

You're also going to need yor own workflow file. Here's a sample:

```yaml
name: Generate Feed
on: [push]
jobs:
  generate-feed:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3
      - name: Run Feed Generator
        uses: ptarasyuk/podcast-generator@main
```
