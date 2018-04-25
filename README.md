# Domain Resource Application Ontology

The Domain Resource Application Ontology (DRAO) is an application ontology describing cross-discipline research domains used within [FAIRsharing]((https://www.fairsharing.org)) records by curators and the user community (see also the [DRAO FAIRsharing record](https://fairsharing.org/bsg-s001178)). It is built in conjunction with the Subject Resource Application Ontology (SRAO), which describes higher-level subject areas / disciplines.

All classes within DRAO come from publicly-available ontologies. Currently, the following ontologies are used to build DRAO: AERO, BFO, CHEBI, CHEMINF, CHMO, CL, CLO, CMO, DOID, DRON, EDAM, EFO, ENVO, EO, ERO, FBBI, FBCV, FMA, GO, HP, IAO, IDO, IDOMAL, MAMO, MFOEM, MI, MOD, MP, MS, NCBITaxon, NCIT, OAE, OBCS, OBI, OGI, OGMS, OMIT, OMP, PATO, PO, PR, PW, SBO, SIO, SO, STATO, SWO, UBERON, UO, VariO, VO. These ontologies were added to DRAO through semi-automated procedures using Ontofox and Ontodog (see below for details).

[AgroVoc](http://artemide.art.uniroma2.it:8081/agrovoc/agrovoc/en/) classes were manually added as required.

# Files

The simplest way to view DRAO is by using [DRAO-merged.owl](https://github.com/FAIRsharing/domain-ontology/blob/master/DRAO-merged.owl). This file was created by merging the development files into a single document for easier loading within the editor of your choice, such as [Protege](http://protege.stanford.edu/). 

Below are short descriptions of a selection of other files found within this repository, all within the [source-owl](https://github.com/FAIRsharing/domain-ontology/tree/master/source-owl) directory:
- [DRAO.owl](https://github.com/FAIRsharing/domain-ontology/blob/master/source-owl/DRAO.owl) - This is the main development file which imports all required classes and annotations. The only information stored *directly* within this file is metadata about the ontology and the required imports. It is manually edited by our team.
- [DRAO-ontofox-annotation.txt](https://github.com/FAIRsharing/domain-ontology/blob/master/source-owl/DRAO-ontofox-annotation.txt) - The configuration file required by Ontofox for automatically adding annotation from the external ontologies to DRAO. It is maintained and updated by our team.
- [DRAO-external.owl](https://github.com/FAIRsharing/domain-ontology/blob/master/source-owl/DRAO-external.owl) - the file created by Ontofox containing only automatically-generated annotation from the external ontologies (no manual modifications are made to this file).

Further automatically-generated files are stored within the [Ontodog](https://github.com/FAIRsharing/domain-ontology/tree/master/source-owl/Ontodog) subdirectory. More information on their purpose and creation is available below.

# Background

FAIRsharing (https://www.fairsharing.org) is a manually-curated, cross-discipline, searchable portal of three linked registries covering standards, databases and data policies. Every record is designed to be interlinked, providing a detailed description not only of the resource itself, but also its relationship to other resources.

As FAIRsharing has grown, over 1000 domain tags across all areas of research have been added by users and curators. This tagging system, essentially a flat list, has become unwieldy and limited. To provide a hierarchical structure and richer semantics, two application ontologies drawn from multiple community ontologies were created to supplement these user tags. FAIRsharing domain tags are now divided into three separate fields:

- [Subject Resource Application Ontology (SRAO)](https://github.com/FAIRsharing/subject-ontology) - a hierarchy of academic disciplines that formalises the re3data subject list (https://www.re3data.org/browse/by-subject/). Combined with subsets of five additional ontologies, SRAO provides over 350 classes.
- Domain Resource Application Ontology (DRAO) - **This repository.** A hierarchy of specific research domains and descriptors. Over fifty external ontologies are used to provide over 1000 classes.
- Free-text user tags. A small number of FAIRsharing domain tags were not mappable to external ontologies and are retained as user tags. Existing and new user tags may be promoted to either application ontology as required.

# DRAO Curation

FAIRsharing users can add any tags to their records in the "Scope and Data Types" section of a FAIRsharing entry. They can select from any of the pre-existing tags or make their own. If they create a new tag, then FAIRsharing curators assess that tag and, if appropriate, place it within either SRAO or DRAO. Otherwise, it will remain in our manually-curated "User tag" vocabulary.

All classes within DRAO come from publicly-available ontologies. These terms are added to DRAO by editing the [Ontofox configuration file](https://github.com/FAIRsharing/domain-ontology/blob/master/source-owl/DRAO-ontofox-annotation.txt). When Ontofox is run (see the "Build" section below), the resulting output will include the new classes. New FAIRsharing-specific annotation is then added via the Ontodog configuration files. This step is more complex, as the Ontodog tool currently requires a different configuration file for each ontology (in contrast to Ontofox, which allows a single configuration file referencing multiple ontologies). 

Additional FAIRsharing-specific annotation is added manually and stored within [DRAO-manual.owl](https://github.com/FAIRsharing/domain-ontology/blob/master/source-owl/DRAO-manual.owl). Classes in this file are from ontologies which are not loaded within Ontobee, the ontology service used by both Ontofox and Ontodog. 

# Build

Domains are the largest set of tags available when curating FAIRsharing records. The classes used within DRAO are imported from external ontologies using Ontofox, and then appropriate annotation is added to those classes using Ontodog. DRAO is written in OWL and serialized as RDF/XML.

## Tools Used

[Ontofox](http://ontofox.hegroup.org/) and [Ontodog](http://ontodog.hegroup.org/) have been used to build the subset ontology files and associated annotation. [Protege](https://protege.stanford.edu/) (including versions 4.3.0 and 5.2.0) has been used to create the core OWL file and to view, check and merge all development ontology files into a single merged file. 

- [Ontofox](http://ontofox.hegroup.org/) - Xiang Z, Courtot M, Brinkman RR, Ruttenberg A, He Y. OntoFox: web-based support for ontology reuse. 
BMC Research Notes. 2010, 3:175. PMID: 20569493 
- [Ontodog](http://ontodog.hegroup.org/) - Zheng J, Xiang Z, Stoeckert Jr. CJ, He Y. Ontodog: a web-based ontology community view generation tool. 
Bioinformatics. 2014; doi: 10.1093/bioinformatics/btu008. 
- [Protege](http://protege.stanford.edu/) - Musen, M.A. [The Protégé project: A look back and a look forward.](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4883684/) AI Matters. Association of Computing Machinery Specific Interest Group in Artificial Intelligence, 1(4), June 2015. DOI: 10.1145/2557001.25757003.

Further information on the development of DRAO is available from the [Development](https://github.com/FAIRsharing/domain-ontology/blob/master/Development.md) page.

# Usage and License

Within FAIRsharing, DRAO and its associated user tags are used by both curators and our user community to annotation FAIRsharing records. DRAO itself is also available for general use from this repository under a [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license.

# Contact Us

Please feel free to contact us with any comments or suggestions at contact@fairsharing.org.



