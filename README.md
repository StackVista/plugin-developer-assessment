# StackState plugin developer assessment

## Background

StackState is a new brand of IT Operations tool that is designed to rapidly solve or prevent down-time of IT systems. StackState
does this by aggregating information from various sources to produce a real-time, up-to-date picture of an IT landscape
and the associated state of each of it's components. Information is retrieved and stored from source systems via _plugins_. A
StackState plugin is written in Python and retrieves  information from a target system, process it and sends it to the
StackState server.

In this assessment you will code a simple StackState plugin for Twitter.

## Objective

Write a StackState plugin (also called a "check" or "agent check") that retrieves information from Twitter and sends
the information into a StackState server.

There are a few moving parts to this assignment:

* the **Twitter service** and it's public REST API, the source of the information
* a **StackState agent instance** that is able to collect information and send it to a StackState instance
* a **plugin for the StackState agent** that knows how to retrieve information from Twitter (this is what you will write)

### Twitter

You can use the public [Twitter REST API](https://dev.twitter.com/overview/api) for this assignment as well as your own personal Twitter account. If you don't
have one, you can create one for free.

Authentication for the REST API can be done using [OAuth application owner access tokens](https://dev.twitter.com/oauth/overview/application-owner-access-tokens).

### Agent

The StackState agent is [open-source](https://github.com/StackVista/stackstate-agent) and can be downloaded and installed separately. There is a public git repository that contains a Vagrant image for developing and testing with the STS agent, see [this repository](https://github.com/StackVista/plugin-developer-assessment).

### Plugin

Plugins are written in Python 2.7 and will run inside the StackState agent. Documentation about [how to write a StackState agent plugin](https://docs.stackstate.com/develop/developer-guides/agent_check) is also available.

## Assignment

Implement a StackState agent plugin that retrieves information from Twitter and sends this information to StackState.

* Create a metric (count) of a particular set of messages on Twitter, for instance direct messages to yourself or messages mentioning the `@gostackstate` Twitter account.
* Create an event with the latest 10 messages in your account's timeline and send it to StackState. Make sure to report every unique Twitter message only once.

### Testing

When you've written a new check, you'll want to test that it works properly. You can test the integration by running it manually, or writing a unit or integration test for it.

### Vagrant

This repository contains a Vagrant setup so you can get started with the assessment quickly. Using this setup, you can spin up a virtual machine in VirtualBox with a fully functional StackState agent install.

To start the virtual machine, use:

```
vagrant up
```

Log into the box using:

```
vagrant ssh
```

You can change to root with the command:

```
sudo su -
```

once logged into the VM.

## Notes

Keep the following in mind:

* the Twitter REST API implements [rate limiting](https://dev.twitter.com/rest/public/rate-limiting), be sure to not exceed the limit
* StackState plugins are written using Python 2.7


## Delivery

To submit the assessment, email us the Python source code for the plugin.
