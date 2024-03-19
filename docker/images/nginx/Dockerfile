FROM nginx:latest

ARG USER_ID
ARG GROUP_ID

RUN usermod -u $USER_ID www-data && groupmod -g $GROUP_ID www-data
