# ec-faq

# Whether EXPRESSCLUSTER mirroring provide database replication for SAP HANA?

Typical usage of HANA is in-memory database and it uses HSR (HANA System Replication) for replication.
EXPRESSCLUSTER is combined with HSR to automate the node promotion from secondary to primary in case of HANA failover.
There is no certification by SAP for supporting HANA and HSR. However, EXPRESSCLUSTER and other failover HA cluster products are descrived in the below document ( P.250 - 252 and around) as a complement product for HSR failover automation.

	https://www.sap.com/documents/2017/02/d4cbb865-a67c-0010-82c7-eda71af511fa.html#

That's the current and general situation.

Your intention might be confirming possibility of HANA replication over WAN by EXPRESSCLUSTER Replicator.
Unfortunately there have been no experience for the combination of HANA and EXPRESSCLSUSTER (incl. Replicator) without HSR. But I imagine its downside as below.

Typical use of HANA is in-memory, so, a COMMIT can complete in-memory before in-disk.
This means EC cannot replicate the COMMITted data, because EC acknowledges the data which come from file-system, and this leads inconsistency in case of crash of primary HANA.

From consistency viewpoint, protection for im-memory database by EXPRESSCLUSTER needs some extent of care.

----

# Where can I find the up-to-date manuals for ECX for virtualization?
All the manuals I can find in that area for ECX in a virtual environment are from December 2012 and they are useless for the current Hypervisor versions.

There is no up-to-date on the documents for virtualization you found.
Almost all use cases of EC on hypervisor platform had been in the Guest Level Clustering ( a cluster by 2 virtual machines )and there is no need for dedicated documents for Guest Level Clustering, because there is no difference between physical and virtual machines from EC perspective.
