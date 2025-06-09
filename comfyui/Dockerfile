FROM intel/intel-extension-for-pytorch:2.7.10-xpu

# Optional, might help with memory allocation performance and scalability
RUN apt-get update && \
    apt-get install -y --no-install-recommends --fix-missing libjemalloc-dev
ENV LD_PRELOAD=libjemalloc.so.2

# Download the ComfyUI repository
RUN cat <<EOF > /bin/startup.sh
#!/bin/bash
git status || git clone https://github.com/comfyanonymous/ComfyUI.git /app
pip install -r /app/requirements.txt
python /app/main.py "\$@"
EOF

# Make the startup script executable
RUN chmod 755 /bin/startup.sh

# Set the working directory to /app
WORKDIR /app

# Run ComfyUI with custom parameters
CMD [ "startup.sh", "--highvram", "--use-pytorch-cross-attention", "--listen=0.0.0.0", "--port=8188" ]
