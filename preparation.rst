.. include:: config.rst

Preparation
===========

Install Docker
--------------

You will need admininstration privileges to do this (or have a sys admin do it).
On Debian/Ubuntu flavour machines, install the package docker.io:

.. code:: bash

  sudo apt-get install docker.io

Ensure user is a member of the docker group:

.. code:: bash

  groups

and add docker if that does not appear in the output above.

.. code:: bash

  sudo adduser USERNAME docker

Download docker image
---------------------

Download the latest version of the Pfam curation tools container from Gitlab:

.. parsed-literal::

  docker pull |docker-image-url|

Set up computer
---------------

Choose a directory on your machine where you will run the container; this can be anywhere you
have write access but it's important that you always use this location.

.. code:: bash

  mkdir pfam_curation
  cd pfam_curation

Within that directory create two additional directories: one will contain the sequence files required
by the pfam tools and the other will be a working directory:

.. code:: bash

  mkdir seqlib
  mkdir pfam_data

Also, create a pfam.conf file in the pfam_curation directory. Use this as a template: https://github.com/ProteinsWebTeam/containers/blob/master/PfamCuration/pfam.conf.example  

Obtain the pfamseq (and, optionally) the uniprot fasta file. Either download the pfamseq.gz
(and uniprot.gz) files from `Pfam ftp <ftp://ftp.ebi.ac.uk/pub/databases/Pfam/current_release>`_
or run the download script:

.. code:: bash

  bash download_pfamseq.sh

If downloading manually you will need to move to the seqlib directory and uncompress.


