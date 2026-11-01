WordPress Blog Deployment Using AWS Lightsail

This project demonstrates how I deployed a WordPress blog on AWS Lightsail using a pre-configured Bitnami WordPress instance. It includes creating the instance, accessing the website, retrieving the WordPress admin credentials, and creating a backup snapshot.

Table of Contents

Project Overview

Tech Stack

Prerequisites

Deployment Steps

Screenshots

Optional Improvements

Security Best Practices

Key Learnings

Author

Project Overview

AWS Lightsail offers easy-to-launch virtual private servers (VPS) with predictable pricing. It is a convenient option for hosting small applications, including WordPress websites.

Project Goal: Set up a functional WordPress blog on AWS Lightsail and create an instance snapshot for backup.

Tech Stack

Component

Details

Cloud Provider

AWS Lightsail

Application

WordPress (Bitnami stack)

Operating System

Linux (Debian-based Bitnami image)

Access

Browser and SSH (Lightsail browser-based terminal)

Backup

Lightsail Instance Snapshot

Prerequisites

An active AWS account

A web browser

Basic knowledge of Linux commands

Deployment Steps

1. Sign in to AWS and open Lightsail

Open the AWS Lightsail Console.

Click Create instance.

2. Choose an instance location

Select the AWS Region closest to your target audience for better performance.

3. Select an instance image

Choose Apps + OS, then select WordPress.

Alternatively, choose OS Only if you want a fully custom setup.

4. Choose an instance plan

Select a plan based on your expected traffic.

The smallest plan is enough for a small blog.

5. Name and create the instance

Give the instance a meaningful name, for example manju-wordpress-blog.

Click Create instance and wait for it to reach the Running state.

6. Access the WordPress site

Open the instance and copy its public IP address.

Paste it into your browser to see the WordPress welcome page.

7. Retrieve the WordPress admin credentials

Click Connect using SSH in the Lightsail console.

Run:

cat bitnami_application_password

Use the password to log in at:

http://<your-public-ip>/wp-admin/

Default username: user

8. Back up the instance

Go to the instance's Snapshots tab.

Click Create snapshot and give it a name.

Optionally, enable automatic snapshots.

Screenshots

1. WordPress default welcome page

The WordPress website is successfully accessible using the instance's public IP address.



2. WordPress admin login page

The WordPress administrator login page can be opened using the /wp-admin/ path.



3. Instance snapshot

An instance snapshot was created through the AWS Lightsail console to preserve a backup.



Optional Improvements

These steps are recommended for a production setup. They are not covered by the screenshots above.

Attach a static IP

By default, the public IP can change after a stop/start. In the Lightsail Networking tab, create a static IP and attach it to the instance.

Use a custom domain

Register a domain (for example through Amazon Route 53) and point its A record to the static IP.

Enable HTTPS with Let's Encrypt

Run the Bitnami certificate tool over SSH and follow the prompts:

sudo /opt/bitnami/bncert-tool

Optimize performance

Use a caching plugin such as W3 Total Cache or LiteSpeed Cache.

Security Best Practices

Keep WordPress core, themes, and plugins updated.

Install a security plugin such as Wordfence.

Change the default admin password after the first login.

Restrict SSH access in the Lightsail firewall settings.

Take regular snapshots (or enable automatic snapshots).

Never commit passwords or keys to this repository.

What I Learned

How to launch a managed WordPress application on a cloud VPS

How to connect to a cloud instance through SSH and access server files

The difference between public and static IP addresses

How to create instance snapshots for backups

Basic WordPress security and performance practices

Author

Manju Gowda
GitHub: manjugowda0007
