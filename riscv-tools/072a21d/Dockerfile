FROM base:latest

# Update RISCV/PATH vars for RISCV toolchain
ENV RISCV="/usr/bin/riscv-tools"
ENV PATH="$RISCV/bin:$PATH"

# Install riscv-tools
RUN git clone https://github.com/riscv/riscv-tools.git /tmp/riscv-tools\
    && cd /tmp/riscv-tools \
    && git checkout 072a21d182ad387a55a1e4b978353efb53ff5841 \
    && git submodule update --init --recursive \
    && ./build.sh \
    && rm -rf /tmp/riscv-tools
