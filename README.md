Oersetter Models
=================

 Maarten van Gompel
 Centre for Language and Speech Technology
 Radboud University Nijmegen
 Licensed under [OPEN LICENCE TO BE DETERMINED BY FRYSKE AKADEMY]

This repository contains models for Oersetter, the Frisian-Dutch Machine
Translation system developed by Radboud University Nijmegen in close
collaboration with Fryske Akademy. This repository does not contain the
literary sources to the models, as supplied by the Fryske Akademy, as those are
copyrighted. It only contains derivative data from which the sources can not be
reconstructed.

It contains the following

* ``nl-fy`` - *Dutch to Frisian*
    * ``moses.ini`` - Configuration for [Moses](http://www.statmt.org/moses/) with parameters optimized on a held-out development set using MERT. This file references all the others, please read the notices inside.
    * ``fy.lm`` - Language model (ARPA-style, generated with SRILM, should run also with KenLM supplied with Moses)
    * ``phrase-table.gz`` - The phrase-translation table (ARPA-style, generated with SRILM, should run also with KenLM supplied with Moses)
    * ``reordering-table.wbe-msd-bidirectional-fe.gz`` - Reordering table
* ``fy-nl`` - *Frisian to Dutch*
    * ``moses.ini`` - Configuration for [Moses](http://www.statmt.org/moses/) with parameters optimized on a held-out development set using MERT. This file references all the others, please read the notices inside.
    * ``nl.lm.gz`` - Language model (ARPA-style, generated with SRILM, should run also with KenLM supplied with Moses), this is a big one trained on the frisian parallel corpora, OpenSubtitles and Europarl
        * ``nl.tiny.lm`` - A small language model trained only on the frisian parallel corpora and used during testing
    * ``phrase-table.gz`` - The phrase-translation table (ARPA-style, generated with SRILM, should run also with KenLM supplied with Moses)
    * ``reordering-table.wbe-msd-bidirectional-fe.gz`` - Reordering table

This system is to be used with [Moses](http://www.statmt.org/moses/). A moses2
server can then be started as follows:

```
moses2 -f moses.ini --server --server-port 2002 --mark-unknown --unknown-word-prefix "<em>" --unknown-word-suffix "</em>"
```

A RESTful webservice wrapper that communicates with such a Moses server (and
also provides a web-interface for users) is provided
[separately](https://github.com/proycon/oersetter-webservice) and is powered by
[CLAM](https://proycon.github.io/clam).

