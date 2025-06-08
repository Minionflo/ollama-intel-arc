FROM intel/intel-extension-for-pytorch:2.7.10-xpu

ENV USE_XETLA=OFF
ENV SYCL_PI_LEVEL_ZERO_USE_IMMEDIATE_COMMANDLISTS=1
ENV SYCL_CACHE_PERSISTENT=1

# Install required packages
RUN apt-get update && apt-get install -y ffmpeg

# Download the Whisper repository
RUN pip install --upgrade pip && pip install -U openai-whisper

# Set the working directory to /app
WORKDIR /app

CMD ["tail", "-f", "/dev/null"]
