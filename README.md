# R-VCF
#安装
#install.packages("vcfR")
library(vcfR)

setwd("D:/文献相关河南大学硕士/R语言需要用到的数据/CAN25/")
#读取
vcf <- read.vcfR("CAN25.vcf")

#查看基本信息
vcf

#查看各部分
head(vcf@meta)  #meta信息（##开头的行）
head(vcf@fix)     #固定字段：CHROM, POS, ID, REF, ALT, QUAL, FILTER, INFO
head(vcf@gt)         #基因型字段（GT列）

#转为数据框
vcf_fix <- as.data.frame(vcf@fix)
vcf_gt  <- as.data.frame(vcf@gt)

#合并fix和gt
vcf_df <- cbind(vcf_fix, vcf_gt)
head(vcf_df)

# 查看变异数量
nrow(vcf_fix)
write.csv(vcf_df,"vcf_df.csv")
