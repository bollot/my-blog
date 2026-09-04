---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
categories: ["摄影"]
tags: []
location: ""
camera: ""
lens: ""
summary: ""
cover:
  image: ""
  alt: ""
  caption: ""
  relative: false
---

{{< gallery >}}
{{< figure src="/images/photo-placeholder.jpg" alt="照片描述" caption="照片说明" >}}
{{< /gallery >}}
