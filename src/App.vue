<template>
  <div class="container">
    <div class="card">
      <h1>QR Code Generator</h1>
      <p class="subtitle">Fetch and display QR codes instantly</p>
      
      <button 
        @click="fetchQRCode" 
        :disabled="loading"
        class="btn"
        id="fetch-qr-button"
      >
        <span v-if="loading" class="spinner"></span>
        {{ loading ? 'Fetching...' : 'Generate QR Code' }}
      </button>
      
      <div v-if="error" class="error">
        {{ error }}
      </div>
      
      <div v-if="success" class="success">
        {{ success }}
      </div>
      
      <div v-if="qrCodeData" class="qr-container">
        <canvas ref="qrCanvas" id="qr-canvas"></canvas>
        <div class="qr-data">
          <strong>QR Data:</strong><br>
          {{ qrCodeData }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, nextTick } from 'vue'
import QRCode from 'qrcode'

export default {
  name: 'App',
  setup() {
    const qrCodeData = ref('')
    const loading = ref(false)
    const error = ref('')
    const success = ref('')
    const qrCanvas = ref(null)

    const fetchQRCode = async () => {
      loading.value = true
      error.value = ''
      success.value = ''
      qrCodeData.value = ''
      
      try {
        const response = await fetch('http://api.sangeethnipun.cf/qrcode')
        
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`)
        }
        
        const data = await response.json()
        
        if (data.success && data.qrcode) {
          qrCodeData.value = data.qrcode
          success.value = data.message || 'QR code retrieved successfully'
          
          // Wait for DOM to update before drawing on canvas
          await nextTick()
          
          // Generate QR code on canvas
          if (qrCanvas.value) {
            await QRCode.toCanvas(qrCanvas.value, data.qrcode, {
              width: 300,
              margin: 2,
              color: {
                dark: '#1a1f3a',
                light: '#ffffff'
              }
            })
          }
        } else {
          throw new Error('Invalid response format')
        }
      } catch (err) {
        error.value = `Error fetching QR code: ${err.message}`
        console.error('Error:', err)
      } finally {
        loading.value = false
      }
    }

    return {
      qrCodeData,
      loading,
      error,
      success,
      qrCanvas,
      fetchQRCode
    }
  }
}
</script>
