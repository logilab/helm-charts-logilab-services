FROM inseefrlab/onyxia-python-datascience

USER root

COPY . /srv/
RUN pip install -U jupyterlab ipywidgets voila --no-cache
RUN if [ -f "/srv/requirements.txt" ]; then pip --no-cache install -U -r /srv/requirements.txt; fi
RUN if [ -f "/srv/environment.yml" ]; then conda env update -n root -f /srv/environment.yml; \
    echo "Warning; Issues may arise when using pip and conda together."; fi
RUN mkdir -p /home/onyxia/.jupyter
RUN if [ -f "/srv/jupyter_config.py" ]; then cp /srv/jupyter_config.py /home/onyxia/.jupyter/; fi
RUN if [ -f "/srv/jupyter_config.json" ]; then cp /srv/jupyter_config.json /home/onyxia/.jupyter/; fi
RUN if [ -f "/srv/jupyter_lab_config.py" ]; then cp /srv/jupyter_lab_config.py /home/onyxia/.jupyter/; fi

RUN sed -i "s|$HOME/work|/srv|g" /opt/onyxia-init.sh

USER 1000
EXPOSE 8888

CMD ["voila", "/srv/voila-vuetify.ipynb", "--Voila.ip='0.0.0.0'", "--port=8888", "--no-browser"]
