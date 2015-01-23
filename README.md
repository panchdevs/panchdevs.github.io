# panchdevs.github.io

This is source for the [PanchDevs blog](https://panchdevs.github.io).

## Instructions

1. Install `ruby`
2. Install `jekyll` with
`gem install jekyll`
3. Clone this repository with
`git clone https://github.com/panchdevs/panchdevs.github.io.git`
4. `cd` into the cloned directory
5. Run the server with
`jekyll serve`

#### OR

If you have some problem with the above instructions you can use a Docker image with jekyll installed instead.

1. Download and install [Docker](http://docs.docker.com/installation/#installation)
2. If required, set the proxy settings as mentioned [here](https://docs.docker.com/articles/systemd/#http-proxy)
3. Pull [this Docker image](https://registry.hub.docker.com/u/jclagache/github-pages/) with
`sudo docker pull jclagache/github-pages`
4. Clone this repository with
`git clone https://github.com/panchdevs/panchdevs.github.io.git`
5. `cd` into the cloned directory
6. Run server with
`sudo docker run --rm -p 4000:4000 -v "$PWD:/src" jclagache/github-pages serve`
