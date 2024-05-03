FROM inseefrlab/onyxia-python-datascience

USER root

COPY . /srv/
RUN pip install -U jupyterlab ipywidgets voila --no-cache
RUN if [ -f "/srv/requirements.txt" ]; then pip --no-cache install -U -r /srv/requirements.txt; fi

USER 1000
EXPOSE 8888

CMD ["voila", "/srv/index.ipynb", "--Voila.ip='0.0.0.0'", "--port=8888", "--no-browser"]
