<script setup lang="ts">
import axios from 'axios'
import { ref } from 'vue'
import Swal from 'sweetalert2'

const form = ref({
  title: '',
  message: ''
})

const validateForm = () => {
  if (!form.value.title || !form.value.message) {
    Swal.fire({
      icon: 'warning',
      title: 'Incomplete Form',
      text: 'Please fill in all required fields.'
    })
    return false
  }
  return true
}

const url = 'https://discord.com/api/webhooks/1430733431381430352/GnFEMFkXJuhHlpMajL3R75mBWyA9lYgRqqTV0HknZ-iTpixyPAoCPg0t_sSSvXU5EYOC' || 'https://discord.com/api/webhooks/1430744698783535214/6mw1krucWcA-1P8rocxO12QutzGdeiCWLSlpDdeiPjGeE3-iI89JKouv8UT8egSWnFY6'

const submit = async () => {
  if (!validateForm()) return

  // ✅ Discord requires a 'content' field
  const payLoad = {
    content: `**Feedback Title:** ${form.value.title}\n**Message:** ${form.value.message}`
  }

  try {
    await axios.post(url, payLoad, {
      headers: {
        'Content-Type': 'application/json',
        Accept: 'application/json'
      }
    })

    Swal.fire({
      icon: 'success',
      title: 'Feedback Sent!',
      text: 'Your feedback has been successfully sent to Discord.'
    })

    form.value.title = ''
    form.value.message = ''
  } catch (error) {
    Swal.fire({
      icon: 'error',
      title: 'Oops...',
      text: 'Failed to send feedback.'
    })
    console.error('Discord Error:', error)
  }
}
</script>

<template>
  <div class="container py-5" style="background-color: #D8B806; min-height: 100vh;">
    <img src="/images/logo-2 1.png" alt="Busanga Logo" class="mx-auto d-block mb-4" style="width: 150px;" />
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card shadow border-0">
          <div class="card-body p-4">
            <h2 class="text-center mb-4 text-primary">Feedback Form</h2>

            <form @submit.prevent="submit">
              <div class="mb-3">
                <label for="feedbackTitle" class="form-label">Feedback Title</label>
                <input 
                  type="text"
                  v-model="form.title"
                  id="feedbackTitle"
                  class="form-control"
                  placeholder="Enter feedback title"
                />
              </div>

              <div class="mb-3">
                <label for="feedbackMessage" class="form-label">Your Feedback</label>
                <textarea 
                  id="feedbackMessage"
                  v-model="form.message"
                  class="form-control"
                  rows="4"
                  placeholder="Write your feedback here..."
                ></textarea>
              </div>

              <button type="submit" class="btn btn-primary w-100">
                Submit Feedback
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
