<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm @submit:contact="addContact" :contact="contact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ đã được thêm thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    },
    data() {
        return {
            contact: [],
            message: "",
        };
    },
};
</script>