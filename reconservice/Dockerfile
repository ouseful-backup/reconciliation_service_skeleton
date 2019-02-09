FROM jupyter/minimal-notebook
MAINTAINER tony.hirst@gmail.com

RUN pip install --no-cache jupyter_kernel_gateway pandas fuzzywuzzy

COPY api_nb /home/jovyan/work/

EXPOSE 8895

CMD  jupyter kernelgateway --ip 0.0.0.0 --KernelGatewayApp.api='kernel_gateway.notebook_http' --KernelGatewayApp.seed_uri='/home/jovyan/work/Reconciler.ipynb' --port 8895

