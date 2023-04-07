# anandamide
Sequencing of RNase A treated Pfizer bivalent vaccines reveals paired-end sequencing evidence of circular plasmids and an inter-vial 72bp variation in the SV40 promoter.

Data preserved from the [Anandamide 11 March 2023 substack.](https://anandamide.substack.com/p/sequencing-of-rnase-a-treated-pfizer)

BAM files

contig specific BAM files were created using samtools

```
samtools view -h input.bam contig_name -O BAM > contig.bam; samtools index contig.bam;
```

Samtools stats run on a each contig in each assembly.

```
for out_prefix in `ls *.sort.bam | perl -pe "s/.sort.bam//"`; do mkdir -p ${out_prefix}-samtools-stats; for contig in `samtools view -H ${out_prefix}.sort.bam  | grep "^@SQ"  | cut -f 2 | perl -pe "s/SN\://"`; do echo "Now calculating stats for ${contig}/$out_prefix..."; samtools stats ${out_prefix}.sort.bam $contig > ${out_prefix}-samtools-stats/${contig}-samtools-stats.txt; done; done
```

* [Pbiv1_RNase_WM_k141_107.fa](../master/Pbiv1_RNase_WM_k141_107.fa)
* [Pbiv1_WM_k141_107.bam](../master/Pbiv1_WM_k141_107.bam)
* [Pbiv1_WM_k141_107.bam.bai](../master/Pbiv1_WM_k141_107.bam.bai)
* [Pbiv2_WM_k141_23.bam](../master/Pbiv2_WM_k141_23.bam)
* [Pbiv2_WM_k141_23.bam.bai](../master/Pbiv2_WM_k141_23.bam.bai)
* [Pbiv2_WM_k141_23.fa](../master/Pbiv2_WM_k141_23.fa)
