solrmarc-rda
============

SolrMarc scripts for determining Format using RDA 33x fields

Auburn University Libraries uses SolrMarc to load data from our Voyager database to our VuFind catalog search.

Determining item formats (especially for faceting) is complicated through MARC because it contains several legacy options for denoting object types. See the default, generic, complex VuFind script in SolrMarc to determine format: https://code.google.com/p/solrmarc/source/browse/trunk/examples/GenericVuFind/index_scripts/format.bsh

The new RDA 33x fields offer a more controlled way of determining most formats. We set about creating a new Format field based on the 338 Carrier Type field. Many formats are represented directly in this field, which can greatly reduce the complexity of format parsing code. But not all typical format types are represented in this field.

Volume is an unmediated carrier type. Patrons of academic libraries don't know the definition of "Volume" though. They will expect to see more specific formats: Books, eBooks, Newspapers, Journals, Theses and Dissertations, which all are classified as Volumes. We created a new indexing script that starts with 338a as the basic format, and then breaks down Volume into its more specific types (by looking elsewhere in the MARC record).

