# rails-docker-template

This is a basis for creating a Ruby on Rails development environment using Docker.

## How does it works?

This provides a template for a `Dockerfile` in which your Rails app can run.  It also provides a template for a
`docker-compose.yml` file you can use to run dependent services, in this case Postgresqle.

It permits to run the Docker container as the Current Host User or any other.

## How to Use

1. Make sure Docker is installed
1. Clone this repo
1. Open `bin/vars` and edit the values in there as instructed.  You should only need to change `ACCOUNT`, `REPO`,
   and `TAG`. And for the User, the login name, UID, group name and GID
1. Run `bin/build`
1. Run `bin/start`
1. In another terminal, run `bin/exec bash`.  You will now be "logged in" to the Docker container where your app
   can run.  This Docker container has:
   * Ruby & Bundler
   * Rails

## Helpful Notes

Inside the container, you can connect to Postgres like so:

```
> PGPASSWORD=postgres psql --host db --username postgres --port 5432
postgres=#
```

When you run Rails, you need to tell it to bind to `0.0.0.0`, so you can't just do `bin/rails s`.  Instead you
must:
```
> bin/rails s --binding 0.0.0.0
```

## Thanks
It is based on https://github.com/sustainable-rails/sustainable-rails-docker created by [davetron5000](/[guides/content/editing-an-existing-page](https://github.com/sustainable-rails/sustainable-rails-docker)https://github.com/sustainable-rails/sustainable-rails-docker).

