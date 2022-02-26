# 👷 Terraforming a Ghost Blog (Digitalocean, Cloudflare, Docker Compose, Cloud-Init)

A starter template to automatically deploy a Ghost Blog on Digitalocean and Cloudflare. The configuration includes [Commento](https://commento.io/), allowing visitors to leave comments to your posts

>  :warning: *Important* : this is a work in progress. The configuration is not fully hardened for a production deployment. You are welcome to leave feedback on areas of improvement or contribute by opening a PR.
## Documentation

This template is fully explained in the tutorial published on my blog

- *Part 1*: [Terraforming a Ghost blog with Docker Compose and Cloudflare - PART 1](https://www.paolotagliaferri.com/ghost-blog-with-terraform-and-docker-compose-digitalocean-cloudflare/)
- *Part 2*: [Terraforming Ghost: Secure origin connection - PART 2](https://www.paolotagliaferri.com/ghost-blog-with-terraform-and-docker-compose-digitalocean-cloudflare-part-2-secure-origin-connection/)
- *Part 3*: [Terraforming Ghost: Persistent volume - PART 3](https://www.paolotagliaferri.com)

## License
This work is available under [MIT License](https://github.com/Vortexmind/terraforming-ghost/blob/main/LICENSE)

### How I use it

1. Create an ubuntu machine as DigitalOcean Droplet
2. git clone https://github.com/cmy113/terraforming-ghost.git
3. Get the DigitalOcean token to create volume
4. `export DO_TOKEN='xxxx'`
5. `cd terraforming-ghost/scripts`
6. `./manage_volume.sh -o create -r sgp1 -s 10 -n ghostvol`
7. Install terraform
8. `curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -`
9. `sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main"`
10. `apt install terraform=0.13.4`
11. Make sure you are in terraforming-ghost directory now by cd .., pwd -> terraforming-ghost
12. nano terraform.tfvars, put in the right variable by following Paolo's blog
13. `terraform init`
14. `terraform plan`
15. `terraform apply`
16. ssh into the target server and tail the log, it should take about 10 minutes! Be patient :)
17. `ssh root@xxxx`
18. `tail -f /var/log/cloud-init-output.log`