# GG-Extract-Replicate
Repository contain Golden Gate config files and parameters
We have 4 Extract Process 
1.>  ECLPDBQB
2.>  ECLPDBQD
3.>  ECLPDBQS
4.>  ECLPFHIR

Parameter file for Process ECLPDBQB

EXTRACT eclpdbqb
USERIDALIAS clprdbq DOMAIN OracleGoldenGate
--TRANLOGOPTIONS INTEGRATEDPARAMS (max_sga_size 35840)
REPORTCOUNT EVERY 10 MINUTES, RATE
EXTTRAIL eb
DDL INCLUDE MAPPED
INCLUDE /data/ggsm01/etc/conf/ogg/prd_tbls_ex_big.txt


Parameter file for Process ECLPDBQD

EXTRACT ECLPDBQD
USERIDALIAS clprdbq DOMAIN OracleGoldenGate
EXTTRAIL eg
--TRANLOGOPTIONS INTEGRATEDPARAMS (MAX_SGA_SIZE 24432, PARALLELISM 2)
DDL INCLUDE MAPPED
INCLUDE /data/ggsm01/etc/conf/ogg/prd_tbls_ex_dag.txt

Parameter file for Process ECLPDBQS

EXTRACT eclpdbqs
USERIDALIAS clprdbq DOMAIN OracleGoldenGate
REPORTCOUNT EVERY 10 MINUTES, RATE
EXTTRAIL es
--TRANLOGOPTIONS CHECKPOINTRETENTIONTIME 3
--TRANLOGOPTIONS INTEGRATEDPARAMS (MAX_SGA_SIZE 2048)
DDL INCLUDE MAPPED
INCLUDE /data/ggsm01/etc/conf/ogg/prd_tbls_ex_small.txt

Parameter file for Process ECLPFHIR

EXTRACT ECLPFHIR
USERIDALIAS clprdbq DOMAIN OracleGoldenGate
---TRANLOGOPTIONS INTEGRATEDPARAMS (max_sga_size 12228)
---TRANLOGOPTIONS INTEGRATEDPARAMS (max_sga_size 8192)    ---> krishna reverted back to 8gb on 30th Jan 2026
REPORTCOUNT EVERY 10 MINUTES, RATE
EXTTRAIL ef
DDL INCLUDE MAPPED
INCLUDE /data/ggsm01/etc/conf/ogg/prd_tbls_ex_fhir.txt



