A skeleton for creating an OpenRefine reconciliation service via a docker container (originally based on [OpenRefine/reconciliation_service_skeleton](https://github.com/OpenRefine/reconciliation_service_skeleton) and also drawing inspiration from [OpenRefine Style Reconciliation Containers](http://blog.ouseful.info/2015/02/02/openrefine-style-reconciliation-containers/)


The services uses a Flask app running by default on port 5000.

To run the container using a CSV based reconciliation file `/path/to/myfile.csv', with column name *Searchval* for the column to fuzzily match against and *Idval* as the *id* value:

`docker run --name reconpy -p 5001:5000 -d -v /path/to:/tmp/import -e RECONFILE=myfile.csv -e SEARCHCOL=Searchval -e IDCOL=Idval psychemedia/recon-py`

For example:

`docker run --name reconpy -p 5001:5000 -d -v `pwd`:/tmp/import -e RECONFILE=UK-MPs.csv -e SEARCHCOL=DisplayAs -e IDCOL=Member_Id psychemedia/recon-py`

and try to reconcile on a name such as `Diana Abbot`.

The `docker-compose` file creates a network between three containers:

- OpenRefine
- Jupyter notebook
- reconciler

The demo notebook is not currently installed in the Jupyter notebook container - you'll have to upload it yourself or create a new one. The one in the repo shows how to connect (ports inside the docker-compose network are the internal ports, not port mapped ports).

The Jupyter notebook can see the reconcile service but OpenRefine appears not to when I try to add it as a reconciliation service.


See [OpenRefine/reconciliation_service_skeleton](https://github.com/OpenRefine/reconciliation_service_skeleton) for additional ideas about how to further use the service, including constructing your own reconciliation service containers.

