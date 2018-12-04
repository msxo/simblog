---
title: JPA OneToMany
tags:
  - JPA
categories:
  - SpringBoot
abbrlink: 8646
date: 2018-11-06 14:09:05
---

> 一对多的逻辑关系 `OnetoMany`，`One`作为处理类。
```java
    @OneToMany(cascade = {
        CascadeType.PERSIST,
        CascadeType.MERGE,
        CascadeType.REMOVE
    }, orphanRemoval = true)
    @JoinColumn(name = "card_configuration_id")
    private List<CardStoreConfiguration> cardStoreConfiguration = new ArrayList<>();
```
- CascadeType.PERSIST 保存
- CascadeType.MERGE  更新
- CascadeType.REMOVE 删除
- orphanRemoval = true 物理删除级联
- orphanRemoval = false 逻辑删除级联

---
> `card_configuration_id` 可以为空。逻辑删除级联时，会将 `card_configuration_id` 变为null.

> 在 `CardStoreConfiguration` 不要有 `card_configuration_id` 对应的字段