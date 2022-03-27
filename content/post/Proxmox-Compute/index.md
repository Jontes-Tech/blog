+++
author = "Jonatan Holmgren"
title = "Proxmox Compute"
date = "2022-03-18"
description = "Use Proxmox for multi-user datacenter compute"
cover="proxmox.webp"
categories = [
    "servers"
]
tags = [
    "proxmox",
]
+++
## What's Proxmox?
Proxmox is a type 1 hypervisor, meaning that the thing that runs VMs is on OS-level. That's cool I thought. Now what the actual crap can we use this for?

## Today's usecase
Today we will use Proxmox on one or multiple clustered compute PCs designed to run C++, Matlab and other pieces of code. As this workload is very CPU intensive, it is perfect for virtualization, since users might want to run their own code that for example only runs on Windows, maybe it is more efficient to run on something like Debian with Docker installed or why not regular old "baremetal" programs on Debian? In today's blog post I will also be covering how to use a GPU that's passed through to a Virtual machine for GPU-heavy applications, even if it's not the goal of this cluster.

## What we need
1. Any USB drive bigger than let's say 8GB for burning the install media
2. A computer with the specs listed in the next segment
3. About 1 hour of configuration time

## Recommended PC Specs
1. 64 Bit AMD or Intel PC with Virtualization capabilities.
2. 16GB Ram for a few VMs, the more the better.
3. 2 2TB NVME SSDs for plenty of storage. This will be raided. Also we want a smaller, prefferably SSD disk to use as the proxmox disk.
4. If GPU passthrough is interesting to you, 2 graphics cards are recommended. One for the proxmox terminal and the other for the VM
5. The usual PC componenets like a mobo with Virtualization capabilities.
  
# Get started

## Flashing the USB 
We download balena etcher from [here](https://www.balena.io/etcher/) and the Proxmox ISO from [here](https://www.proxmox.com/en/downloads). Now we will flash this ISO file onto the USB drive with balena etcher, if this is complicated to you, I suggest following the steps in [this video](https://www.youtube.com/watch?v=__YyFBRvj3o)

## Getting into the BIOS/UEFI
Repeatedly spam the `delete` key, the `escape` key or one of the `f` keys. From now on I will call this interface the "Bios", even if on newer systems the correct term is UEFI, just to make things easier.  
You should now look for `Secure Boot`, and turn it off, this will make our lives a hell of a lot easier. Also enable `AMD-V` or `Intel VT` depending on if you're team red or team blue. After this we are ready to boot into the USB drive we created with Balena Etcher. Plug it into your PC and find a way to boot into it.

## The installation process
The install wizard should be fairly straight forward, after you are done with it it should show you a URL, so navigate into this using a web browser on your main computer. Now log in with username: `root` and the password you chose.

## Clustering
Skip this part if you only have 1 server.
If there is multiple we will cluster them together with the help of [a tutorial from LearnLinuxTV](https://www.youtube.com/watch?v=QWyLilz1RqU)

## Preparing for creating our first VM
We will have to enable storing VM disks on your SSDs, so this is how. 
Make sure you are in `Server View`, then click `Datacenter`, `storage`, `local` and then `edit`. Enable `Disk Image` in there.

## Downloading the ISO files for the OSes we will install.
Go download Microsoft Windows, Debian, I don't care. Choose whatever OS you want your first VM to run.
Click `ISO Images` in `local` in the Server view. Now upload these images!

## Creating our first VM
Now click "Create a VM" and follow the wisard. You can duplicate these VMs to create multiple with the same OS. Fun, isn't it?

## How about the GPU passthrough you promised?
[This amazing video by TechnoTim](https://www.youtube.com/watch?v=fgx3NMk6F54) shows how to create this.

## Summary
I love Proxmox, and I think you will too! This is a really fun project to give a go!

If this helped you, please share my blog with your friends and colleagues, as I would greatly appriciate that.

If there is any questions you can email me at [support@jontes.page](mailto:support@jontes.page).

Kind regards, Jonte.