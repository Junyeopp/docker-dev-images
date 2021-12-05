
FROM python:3.9-slim-bullseye

WORKDIR /tmp
RUN python -m pip install --upgrade pip \
    && python -m pip install pipenv

RUN apt-get update \
    && apt-get install -y gcc less gpg sudo curl vim unzip

RUN echo 'deb http://download.opensuse.org/repositories/shells:/fish:/release:/3/Debian_11/ /' | tee /etc/apt/sources.list.d/shells:fish:release:3.list
RUN curl -fsSL https://download.opensuse.org/repositories/shells:fish:release:3/Debian_11/Release.key | gpg --dearmor | tee /etc/apt/trusted.gpg.d/shells_fish_release_3.gpg > /dev/null
RUN apt update \
    && apt install -y fish

RUN echo /usr/bin/fish | tee -a /etc/shells && chsh -s /usr/bin/fish

COPY Pipfile /tmp/
# RUN pipenv lock
# # COPY Pipfile Pipfile.lock /tmp/
# RUN pipenv install --system --deploy --ignore-pipfile \
# && rm -fr /root/.cache

RUN pipenv install --system --deploy --skip-lock \
    && rm -fr /root/.cache

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install

WORKDIR /root/
RUN mkdir try_everything

ENTRYPOINT ["fish"]
