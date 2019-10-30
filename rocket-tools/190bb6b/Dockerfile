FROM base:latest

# Update RISCV/PATH vars for ROCKET toolchain
ENV RISCV="/usr/bin/rocket-tools"
ENV PATH="$RISCV/bin:$PATH"

# Install riscv-tools
RUN git clone https://github.com/chipsalliance/rocket-tools.git /tmp/rocket-tools\
    && cd /tmp/rocket-tools \
    && git checkout 190bb6badf53673f29611796fa29a8ba7a37f002 \
    && git submodule update --init --recursive \
    && ./build.sh \
    && rm -rf /tmp/rocket-tools
