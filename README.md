# ECS Tile
This is a PCF Tile that generates 3 ECS servers and provisions them for Cloud Foundry. Currently, we require you to build your own [ECS release](https://github.com/EMC-Dojo/ecs-release) into a tarball and then build the tile yourself. We use the [PCF tile generator](https://docs.pivotal.io/tiledev/tile-generator.html#how-to) to build this tile. 

## Steps to construct the tile

1. Install the [BOSH CLI](https://bosh.io/docs/bosh-cli.html).
1. `git clone` the [ECS release repository](https://github.com/EMC-Dojo/ecs-release).
1. cd into the ECS release and type `git submodule update --init --recursive`
1. `git clone` this repository.
1. Inside the ECS Release directory, `bosh create release --with-tarball`. This will create a release tarball that is dumped into the dev_releases directory.
1. Move this tarball into the ecs-tile's Resources directory and rename it `ecs.tgz`.
1. Install the [tile generator python package](https://docs.pivotal.io/tiledev/tile-generator.html#how-to).
1. `tile build` from the ecs-tile repo. 

## How to use the tile

1. Log into PCF Ops Manager.
1. Click on Import a Product.
1. Upload the tile. (The tile has a .pivotal extension.)
1. After it's done uploading, click on the + button to the right of the ECS release listing at the left column.
1. Once the tile shows up in the middle column, click on Apply changes.
1. Once the build goes through (which can take up to half an hour), your ECS should be accessible. 
