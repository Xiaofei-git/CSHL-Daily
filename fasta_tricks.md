```
grep -c "^>" Sspon.HiC_chr_asm_Subgenome_A.fasta #count
grep -e ">" Sspon.HiC_chr_asm_Subgenome_A.fasta #display header

#show id sorted by sequence lenght
awk '/^>/ {printf("%s%s\t",(N>0?"\n":""),$0);N++;next;} {printf("%s",$0);} END {printf("\n");}'  Chloroplast.contigs.NC_005878.2.fa  |awk -F '\t' '{printf("%d\t%s\n",length($2),$0);}' |sort -k1,1n | cut -f 2- | tr "\t" "\n" | tail | grep -e ">"
```

Get unique ids from pfam output
```
#count unique IDs
grep -v "^#" mikado.protein.pfam.out.txt | awk -F" " '{print $1}' | sort | uniq | wc -l

#get unique IDs to a file
grep -v "^#" mikado.protein.pfam.out.txt | awk -F" " '{print $1}' | sort | uniq > mikado.protein.pfam.list.txt
```
