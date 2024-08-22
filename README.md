# Tresor

> A secrets vault for teams

Keep your secrets only visible for your eyes and share them as needed with your
team.

## Motivation

After using some solutions for managing secrets, I saw some problems
regarding security and management capabilities when dealing with a lot of
secrets shared across multiple teams.

Most of the tools I used were proprietary tools or tools, that were not made
for sharing secrets. Especially when it comes to secrets, I think Free and
Open Source Software is the only suitable option. This is where you put your
keys to the kingdom. These tools have to be open for you to review. All of
the code involved.

## Requirements

As I already made some thoughts about storing, sharing and managing
secrets, here is an opinionated list of requirements:

The software should

- be free and Open Source.
- be able to share secrets between individual people and teams.
- provide strong encryption. Only the devices, that will use/read the
  secrets should be able to decrypt the secret.
- keep some fields in cleartext, so you can search without having to
  decrypt everything.
- provide an API for extension.

## Architecture

As some of the requirements say, only the devices reading the secrets should
be able to decrypt them. To achieve this, the secrets should be encrypted using
a symmetric encryption algorithm, such as AES-256 or ChaCha20. The secrets
should organized in collections and for each collection, a encryption
password is generated. This password is then encrypted using asymmetric
encryption for each device a user with access has. When requesting the
secrets, only the encrypted version is going over the wire and is decrypted on
the device using the private key of the asymmetric encryption algorithm.
