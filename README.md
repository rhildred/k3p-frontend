# k3p-frontend
## cloudflare ingress for k3p

TLDR;

```bash
npm install
npm run dev
```

or to run in the debugger 

```bash
```

```bash
npm run deploy
```

This serves static code that is uploaded as a .zip at deployment time to a cloudflare r2 bucket folder with the same name as the host header. Meta information, like the backend to proxy to is stored in a .env file in the usual format.

If there is a GET request it tries to serve the resource from the s3 bucket. If this fails we proxy to the backend in the .env file. 

If there is a put request for an opaque resource in the .env that contains a .zip in it with an auth header matching a secret in the .env it will unpack the .zip to the folder. 

If the .zip file contains a .env file in it with a io.k3p.image value, that image will be put in the backend under the repository owner name as namespace and the repository name as name.

This is meant as a cheap and cheerful way for autonomous teams to provide microfrontends for each other.
