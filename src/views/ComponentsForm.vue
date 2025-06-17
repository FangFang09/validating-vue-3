<template>
  <div>
    <h1>Create an Event</h1>
    <form @submit="onSubmit">
      <BaseSelect
        v-model="category"
        label="Select a category"
        :options="categories"
        :error="errors.category"
      />

      <h3>Name & describe your event</h3>
      <BaseInput
        v-model="title"
        label="Title"
        :error="errors.title"
        type="text"
      />

      <BaseInput
        v-model="description"
        label="Description"
        :error="errors.description"
        type="text"
      />

      <h3>Where is your event?</h3>
      <BaseInput
        v-model="location"
        label="Location"
        :error="errors.location"
        type="text"
      />

      <h3>Are pets allowed?</h3>
      <BaseRadioGroup
        v-model="pets"
        :error="errors.pets"
        name="pets"
        :options="[
          { value: 1, label: 'Yes' },
          { value: 0, label: 'No' },
        ]"
      />

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          v-model="catering"
          label="Catering"
          :error="errors.catering"
        />
      </div>

      <div>
        <BaseCheckbox
          v-model="music"
          label="Live music"
          :error="errors.music"
        />
      </div>

      <div>
        <BaseButton type="submit" class="-fill-gradient" something="else">
          Submit
        </BaseButton>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useField, useForm } from "vee-validate";
import { object, string, number, boolean } from "yup";

const categories = ref([
  "sustainability",
  "nature",
  "animal welfare",
  "housing",
  "education",
  "food",
  "community",
]);

const validationSchema = object({
  category: string().required(),
  title: string().required("a cool title is required!").min(3),
  description: string(),
  location: string(),
  pets: number(),
  catering: boolean(),
  music: boolean(),
});

const { handleSubmit, errors } = useForm({
  validationSchema,
  initialValues: {
    pets: 0,
    catering: false,
    music: false,
  },
});

const onSubmit = handleSubmit(
  (values) => {
    console.log("驗證通過", values);
  },
  (error) => {
    console.log("驗證失敗", error);
  },
);

const { value: category } = useField("category");
const { value: title } = useField("title");
const { value: description } = useField("description");
const { value: location } = useField("location");
const { value: pets } = useField("pets");
const { value: catering } = useField("catering");
const { value: music } = useField("music");
</script>
