---
layout: default
title: Fig CLI reference
---

CLI reference
=============

Most commands are run against one or more services. If the service is omitted, it will apply to all services.

Run `fig [COMMAND] --help` for full usage.

## build

Build or rebuild services.

Services are built once and then tagged as `project_service`, e.g. `figtest_db`. If you change a service's `Dockerfile` or the contents of its build directory, you can run `fig build` to rebuild it.

## help

Get help on a command.

## kill

Force stop service containers.

## logs

View output from services.

## ps

List containers.

## rm

Remove stopped service containers.


## run

Run a one-off command on a service.

For example:

    $ fig run web python manage.py shell

Note that this will not start any services that the command's service links to. So if, for example, your one-off command talks to your database, you will need to run `fig up -d db` first.

## scale

Set number of containers to run for a service.

Numbers are specified in the form `service=num` as arguments.
For example:

    $ fig scale web=2 worker=3

## start

Start existing containers for a service.

## stop

Stop running containers without removing them. They can be started again with `fig start`.

## up

Build, (re)create, start and attach to containers for a service.

By default, `fig up` will aggregate the output of each container, and when it exits, all containers will be stopped. If you run `fig up -d`, it'll start the containers in the background and leave them running.

If there are existing containers for a service, `fig up` will stop and recreate them (preserving mounted volumes with [volumes-from]), so that changes in `fig.yml` are picked up.

[volumes-from]: http://docs.docker.io/en/latest/use/working_with_volumes/
