# Matrix Spec Change Redirector

This is a simple service that redirects URLs to the [official repository](https://github.com/matrix-org/matrix-spec-proposals) for Matrix Spec Changes (MSCs).

An instance is running at https://msc.re.

It's built using the [Caddy] HTTP server for simplicity. See the [Caddyfile](./Caddyfile) for the entire setup.

[Caddy]: https://caddyserver.com/

## How it works

The service listens on a domain and redirects requests to the official repository. For example, a request to `https://msc.re/1234` will be redirected to `https://github.com/matrix-org/matrix-spec-proposals/pulls/1234`.

The following paths are accepted:

- `/` — redirects to the repository's home page
- `/1234`, `/msc1234`, `/MSC1234` (case insensitive) — redirects to the pull request page
  
All other paths return 404 errors.

## Running

To run the service, you'll need to have [Caddy] installed. In the directory of this project, run:

```bash
source .envrc # to load the environment variables
caddy start
```

## Configuration

Some parameters have to be provided as environment variables. 

- `DOMAIN`: The domain to listen on. Defaults to `localhost`.
- `BASE_URL`: The base URL to redirect to. Should be `https://github.com/matrix-org/matrix-spec-proposals`.
- `BASE_PATH`: The path that will be put before the MSC number in the redirect URL. Should be `/pulls`.

## License

This project is licensed under the [MIT License](./LICENSE).

## Contact

Join the Matrix room: [#msc-re:evolved.systems](https://matrix.to/#/#msc-re:evolved.systems).
