FROM base:latest

# Get RISC-V tools, Verilator, and Yosys
ENV INSTALLED_VERILATOR_DIR="/opt/verilator"
ENV INSTALLED_VERILATOR="$INSTALLED_VERILATOR_DIR/verilator"
COPY --from=verilator:4_016 /usr/local/bin/verilator* $INSTALLED_VERILATOR_DIR/
COPY --from=verilator:4_016 /usr/local/share/verilator /usr/local/share/verilator

ENV RISCV="/opt/riscv-tools"
ENV LD_LIBRARY_PATH="$RISCV/lib"
COPY --from=riscv-tools:072a21d /usr/bin/riscv-tools $RISCV

ENV INSTALLED_YOSYS="/opt/yosys"
COPY --from=yosys:latest /opt/yosys $INSTALLED_YOSYS

# Setup path with the installations
ENV PATH="$INSTALLED_VERILATOR_DIR:$RISCV/bin:$INSTALLED_YOSYS/bin:$PATH"

# Setup home and the user
ENV HOME /home/riscvuser
WORKDIR $HOME
USER riscvuser

# Install RocketChip
RUN git clone https://github.com/chipsalliance/rocket-chip.git $HOME/rocket-chip \
    && cd $HOME/rocket-chip \
    && git checkout 4bdf4b9936cb5122075c3f8d57013e02db2a9572 \
    && git submodule update --init --recursive 

CMD ["/bin/sh"]
