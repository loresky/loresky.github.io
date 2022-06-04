+++
title= "Solr分词"
date= "2022-06-04T10:05:26+08:00"
tags = []
featured_image = ""
description = ""
+++

[ik-analyzer-solr地址](https://github.com/magese/ik-analyzer-solr)
[elasticsearch-analysis-ik地址](https://github.com/medcl/elasticsearch-analysis-ik)

**配置Solr的managed-schema，添加ik分词器**

``` xml
<!-- 使用 -->
<field name="id" type="text_ik" uninvertible="true" indexed="true" stored="true"/>
<!-- ik分词器 -->
<fieldType name="text_ik" class="solr.TextField">
  <analyzer type="index">
      <tokenizer class="org.wltea.analyzer.lucene.IKTokenizerFactory" useSmart="false" conf="ik.conf"/>
      <filter class="solr.LowerCaseFilterFactory"/>
  </analyzer>
  <analyzer type="query">
      <tokenizer class="org.wltea.analyzer.lucene.IKTokenizerFactory" useSmart="true" conf="ik.conf"/>
      <filter class="solr.LowerCaseFilterFactory"/>
  </analyzer>
</fieldType>
```

``` xml
<!-- 排序数字会排到字母前面 -->
 <fieldType name="alphaNumericSort" class="solr.TextField" omitNorms="true" sortMissingLast="false">
    <analyzer>
      <tokenizer class="solr.KeywordTokenizerFactory"/>
      <filter class="solr.LowerCaseFilterFactory"/>
      <filter class="solr.TrimFilterFactory"/>
      <filter class="solr.PatternReplaceFilterFactory" pattern="^(a |the |les |la |le |l'|de la |du |des)" replace="all" replacement=""/>
      <filter class="solr.PatternReplaceFilterFactory" pattern="(\d+)" replace="all" replacement="00000$1"/>
      <filter class="solr.PatternReplaceFilterFactory" pattern="0*([0-9]{6,})" replace="all" replacement="$1"/>
      <filter class="solr.PatternReplaceFilterFactory" pattern="([^a-z0-9])" replace="all" replacement=""/>
    </analyzer>
  </fieldType>
```

https://www.cnblogs.com/itdragon/p/8007144.html

https://www.cnblogs.com/itdragon/p/7995040.html