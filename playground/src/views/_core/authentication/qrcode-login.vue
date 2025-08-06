<script lang="ts" setup>
import { AuthenticationQrCodeLogin } from '@oasis/common-ui';
import { LOGIN_PATH } from '@oasis/constants';

defineOptions({ name: 'QrCodeLogin' });
</script>

<template>
  <AuthenticationQrCodeLogin :login-path="LOGIN_PATH" />
</template>
