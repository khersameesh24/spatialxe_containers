FROM julia:1.10.6

RUN apt-get update && apt-get install -y \
    build-essential \
    python3 \
    python3-pip \
    unzip \
    procps \
    && rm -rf /var/lib/apt/lists/*

# install ometiff
RUN julia -e 'using Pkg; Pkg.add("OMETIFF"); Pkg.precompile()'

# download baysor
RUN curl -O -L https://github.com/kharchenkolab/Baysor/releases/download/v0.7.1/baysor-x86_x64-linux-v0.7.1_build.zip && \
    unzip baysor-x86_x64-linux-v0.7.1_build.zip && \
    rm baysor-x86_x64-linux-v0.7.1_build.zip

# add baysor to path as symlink
RUN ln -s /usr/bin/baysor/bin/baysor /usr/local/bin/

# Create a non-root user for security
RUN useradd --create-home gqcuser

WORKDIR /home/gqcuser
