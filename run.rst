.. include:: config.rst

Running the container
=====================

.. parsed-literal::

  docker run --rm -it -v $(pwd)/pfam_data:/home/pfam/pfam_data -v $(pwd)/pfam.conf:/home/pfam/pfam.conf -v $(pwd)/seqlib:/data/seqlib -v $(pwd)/testDB:/home/pfam/test -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix |docker-image-url|

This will give you a command prompt inside the container where you will have access to all the Pfam
curation tools and scripts.

The first time you run you will need to index the sequence file(s) you downloaded previously:

.. code:: bash

   esl-sfetch --index /data/seqlib/pfamseq
   esl-sfetch --index /data/seqlib/uniprot

To exit the container, type control-D.

If you use the directory pfam_data to download and build families, then the files in this directory
will be preserved if you exit the container and re-run later. They will also be accessible from the host
computer in the directory of that name.

The command above should work on Linux-based machines and will permit applications such as belvu to
run correctly. On a Mac the command above will require some modification. If a workaround does not exist,
it's possible to install and run these programs from the host computer. If you change to the pfam_data
directory first it will be equivalent to running the command within the container.

