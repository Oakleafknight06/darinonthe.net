---
date: '{{ .Date }}'
draft: true
layout: 'post'
title: '{{ replace .File.ContentBaseName `-` ` ` | title }}'
---
