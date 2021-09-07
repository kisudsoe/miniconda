# Prepare Bioconda docker - samtools, bcftools, snpeff, multiqc, hapcut2, whatshap, parallel

* Generate Dockerfile: https://stackoverflow.com/questions/58269375/how-to-install-packages-with-miniconda-in-dockerfile
* Build image: https://docs.docker.com/engine/reference/commandline/build/
* Set up BIOCONDA channels: https://bioconda.github.io/user/install.html#set-up-channels

```bash
# Bulid an image
sudo docker build -t kisudsoe/miniconda:latest /skim/postgwas/miniconda

# Run the image
sudo docker run -it kisudsoe/miniconda

# Install programs
apt update && apt upgrade -y
conda install -c bioconda bcftools samtools htslib snpeff multiqc hapcut2 whatshap parallel openssl=1.0
#conda create -n sambcfenv samtools bcftools htslib

# Commit & upload the image
sudo docker commit b6243cd33066 #<- Container ID will be changed.
sudo docker push kisudsoe/miniconda
```

