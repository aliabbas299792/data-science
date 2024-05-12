FROM continuumio/miniconda3:main

# Base utilities
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y bzip2 gcc git htop screen vim wget zsh tree fzf && \
    apt-get clean && \
    rm -rf /var/lib/apts/lists/*

# Oh My Zsh
RUN chsh -s /bin/zsh && \
    zsh && \
    sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" && \
    git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions && \
    echo "source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh" >> "/root/.zshrc"
SHELL ["/bin/zsh", "-c"]

# Conda
RUN conda update -y conda && \
    conda install -y python=3.10 pandas ipython

WORKDIR /root
CMD ["zsh"]