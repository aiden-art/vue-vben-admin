<script setup lang="ts">
import type { SupportedLanguagesType } from '@oasis/locales';

import { SUPPORT_LANGUAGES } from '@oasis/constants';
import { Languages } from '@oasis/icons';
import { loadLocaleMessages } from '@oasis/locales';
import { preferences, updatePreferences } from '@oasis/preferences';

import { VbenDropdownRadioMenu, VbenIconButton } from '@oasis-core/shadcn-ui';

defineOptions({
  name: 'LanguageToggle',
});

async function handleUpdate(value: string | undefined) {
  if (!value) return;
  const locale = value as SupportedLanguagesType;
  updatePreferences({
    app: {
      locale,
    },
  });
  await loadLocaleMessages(locale);
}
</script>

<template>
  <div>
    <VbenDropdownRadioMenu
      :menus="SUPPORT_LANGUAGES"
      :model-value="preferences.app.locale"
      @update:model-value="handleUpdate"
    >
      <VbenIconButton>
        <Languages class="text-foreground size-4" />
      </VbenIconButton>
    </VbenDropdownRadioMenu>
  </div>
</template>
