<template>
  <Layout :title="id ? 'Редактирование записи' : 'Создание записи'">
    <GroupForm
        :id="id"
        @submit="onSubmit"
    />
  </Layout>
</template>

<script>
import { useStore } from 'vuex';

import { updateItem, addItem } from '@/store/groups/selectors';
import Layout from '@/components/Layout/Layout.vue';
import GroupForm from '@/components/GroupForm/GroupForm.vue';
export default {
  name: 'GroupEdit',
  props: {
    id: String,
  },
  components: {
    Layout,
    GroupForm,
  },
  setup() {
    const store = useStore();
    return {
      onSubmit: ({ id, group, speciality }) => id ?
          updateItem(store, { id, group, speciality }) :
          addItem(store, { group, speciality }),
    };
  }
}
</script>

