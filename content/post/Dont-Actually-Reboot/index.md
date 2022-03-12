+++
author = "Jonatan Holmgren"
title = "Don't Actually reboot"
date = "2022-01-25"
description = "Beta utility that asks you if you REALLY want to reboot."
categories = [
    "shellscripts"
]
tags = [
    "shellscripts",
]
image = "light.webp"
+++
So basically I made this utility that asks you if you want to reboot if you run "sudo reboot" instead of doing it right away. You can install it using
`bash -c "$(curl -fsSL https://go.jontes.page/dar.sh)"`

You may also use the bleeding edge with https://go.jontes.page/testdar.sh, but I strongly advice against it. It's full of bugs.

Github: https://github.com/Jontes-Tech/dont-actually-reboot