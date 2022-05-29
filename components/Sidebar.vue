<script setup lang="ts">
// const coreMembers = await $fetch('/api/core-members')
// const friendLink = await $fetch('/api/friend-link')

const [{ data: coreMembers }, { data: friendLink }] = await Promise.all([useFetch('/api/core-members'), useFetch('/api/friend-link')])
// const [{ data: coresRef }, { data: friendsRef }] = await Promise.all([useFetch('/api/core-members'), useFetch('/api/friend-link')])
</script>

<template>
  <div px8 py6 w95 min-h-screen b="l l-gray2 dark:l-gray2/20">
    <div flex justify-between>
      <h2 text-2xl>
        developer-plus
      </h2>
      <div flex items-center text-lg>
        <a icon-primary i-carbon-logo-github mr2 href="https://github.com/developer-plus" target="_blank" />
        <dark-toggle />
      </div>
    </div>

    <div mt4 op70>
      来源于开发者，服务于开发者。
    </div>

    <div mt9>
      <h3 text-xl>
        核心成员
      </h3>

      <div grid="~ cols-5 gap-4" mt2>
        <a v-for="(member, index) in coreMembers" :key="index" :href="member.link" :title="member.name">
          <img class="aspect-1/1" cursor-pointer rounded-full :src="member.avatar" :alt="member.name">
        </a>
      </div>
    </div>

    <div mt9>
      <h3 text-xl>
        加入我们
      </h3>

      <div mt4 op70>
        添加微信号 `Hongbusi16530`，了解更多。
      </div>
    </div>

    <div mt9>
      <h3 text-xl>
        快速入口
      </h3>

      <div flex justify-between mt6>
        <a btn-primary href="https://github.com/developer-plus/weekly/issues/new/choose" target="_blank">
          周刊投稿
        </a>
        <a
          btn-primary
          href="https://github.com/developer-plus/plans/issues/new?assignees=&labels=pr+welcome&template=create.yml&title=%E3%80%90TODO%E3%80%91"
          target="_blank"
        >
          新增计划
        </a>
        <a btn-primary href="https://github.com/developer-plus/developer-plus/issues" target="_blank">
          勘误/建议
        </a>
      </div>
    </div>

    <div mt9>
      <h3 text-xl>
        每日一题
      </h3>

      <div mt4 op70>
        手写题：如何实现防抖节流？
      </div>

      <a btn-primary-small mt4 href="https://github.com/developer-plus/interview/issues/5" target="_blank">
        前往答题
      </a>
    </div>

    <div mt9>
      <h3 text-xl>
        友情链接
      </h3>

      <div mt9>
        <a v-for="item in friendLink" :key="item.link" :href="item.link" target="_blank">
          <div p2 mt2 bg-primary>
            <h2 text-lg>{{ item.title }}</h2>
            <p op-70>{{ item.description }}</p>
          </div>
        </a>
      </div>
    </div>

    <footer text-sm mt10 op70>
      Copyright © 2022 developer-plus, made with 💗.
    </footer>
  </div>
</template>
