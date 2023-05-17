<script setup lang="ts">
const style = {
  backgroundImage: `url("${import.meta.env.BASE_URL}${$slidev.configs.profilePicture}")`,
  backgroundRepeat: "no-repeat",
  backgroundPosition: "center",
  backgroundSize: "cover",
};
</script>
<template>
  <div class="grid grid-cols-2 w-full h-full auto-rows-fr">
    <div class="slidev-layout left-only">
      <div class="my-auto">
        <div class="h-[50px]"/>
        <div class="author h-[50px]"> {{ $slidev.configs.author }}</div>
        <div class="position h-[150px] leading-6">
          {{ $slidev.configs.position }}
          <br/>
          {{ $slidev.configs.position2 }}
          <br/><span class="text-base">at Snowdog</span>
        </div>
        <div>
          <ic-mail-outline/>&nbsp;
          <a href="mailto:{{ $slidev.configs.email }}">{{ $slidev.configs.email }}</a>
        </div>
        <div>
          <mdi-linkedin/>&nbsp;
          <a href="{{ $slidev.configs.linkedin }}" target="_blank">
            Linkedin
          </a>
        </div>
      </div>
    </div>
    <div class="w-full w-full" :style="style"/>
  </div>
</template>
