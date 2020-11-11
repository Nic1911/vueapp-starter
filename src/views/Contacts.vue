<template>
	<div class="contacts">
		<form @submit="checkForm" method="post">

            <p v-if="errors.length">
                <b>Please correct the following error(s):</b>
                <ul>
                    <li v-for="error in errors" :key="error">{{ error }}</li>
                </ul>
            </p>


			<p>
				<label for="name">Name</label>
				<input id="name" v-model="name" type="text" name="name" />
			</p>

			<p>
				<label for="email">Email</label>
				<input id="email" v-model="email" type="email" name="email" />
			</p>

			<div>
				<input type="submit" value="Submit"  />
			</div>
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			errors: [],
			name: null,
			email: null,
		};
	},
	methods: {
		checkForm: function(e) {
            this.errors = [];

            if (!this.name) {
                this.errors.push("Name required.");
            }
            if (!this.email) {
                this.errors.push("Email required.");
            } else if (!this.validEmail(this.email)) {
                this.errors.push("Valid email required.");
            }

            if (!this.errors.length) {
                alert('Thank you!');
                this.$router.push('/');
            }

            e.preventDefault();
        },
        validEmail: function(email) {
            var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(email);
        },
	},
};
</script>
