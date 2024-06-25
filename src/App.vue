<script setup>
import { ref } from 'vue'; 

const response = ref([
{
       "id": 459,
       "parent_id": 0,
       "space_id": 118,
       "instance_user_id": 54,
       "name": "Guidelines",
       "deleted_at": null,
       "created_at": "2024-04-11 17:13:42",
       "updated_at": "2024-04-11 17:14:57"
   },
   {
       "id": 460,
       "parent_id": 459,
       "space_id": 118,
       "instance_user_id": 54,
       "name": "How to communicate in chat and discord in single project perspective",
       "deleted_at": null,
       "created_at": "2024-04-11 17:14:08",
       "updated_at": "2024-04-15 17:27:24"
   },
   {
       "id": 461,
       "parent_id": 459,
       "space_id": 118,
       "instance_user_id": 54,
       "name": "How to use Space",
       "deleted_at": null,
       "created_at": "2024-04-11 17:14:23",
       "updated_at": "2024-04-11 17:50:27"
   },
   {
       "id": 464,
       "parent_id": 461,
       "space_id": 118,
       "instance_user_id": 54,
       "name": "How to track time",
       "deleted_at": null,
       "created_at": "2024-04-11 17:24:01",
       "updated_at": "2024-04-15 16:30:27"
   },
   {
       "id": 465,
       "parent_id": 461,
       "space_id": 118,
       "instance_user_id": 54,
       "name": "How to use project notifications, timer, project statuses, etc",
       "deleted_at": null,
       "created_at": "2024-04-11 17:24:18",
       "updated_at": "2024-04-15 17:12:26"
   },
   {
       "id": 466,
       "parent_id": 464,
       "space_id": 118,
       "instance_user_id": 54,
       "name": "How your commits (tracks) should look",
       "deleted_at": null,
       "created_at": "2024-04-11 18:48:58",
       "updated_at": "2024-04-11 18:51:47"
   },
   {
       "id": 471,
       "parent_id": 0,
       "space_id": 118,
       "instance_user_id": 2,
       "name": "test",
       "deleted_at": null,
       "created_at": "2024-04-24 20:57:56",
       "updated_at": "2024-04-24 20:57:56"
   }
])

const calculateSpaces = (item) => {
  let indentation = 0;
  let parentId = item.parent_id;

  while (parentId !== 0) {
    const parentItem = response.value.find(i => i.id === parentId);
    if (parentItem) {
      indentation += parentItem.space_id/2;
      parentId = parentItem.parent_id;
    } else {
      break;
    }
  }

  return indentation;
};
</script>

<template>
  <div>
      <ul class="items">
        <li v-for="item in response" :key="item.id" :style="{ 'margin-left': calculateSpaces(item) + 'px' }">
          {{ item.name }}
        </li>
      </ul>
  </div>
</template>

<style scoped>
.items {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 15px;
  list-style: disc;
}
</style>
