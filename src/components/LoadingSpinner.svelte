<script>
    export let message = "Loading...";
  </script>
  
  <div class="loading-spinner">
      <div class="spinner"></div>
      <p>{message}</p>
  </div>
  
  <style>
    .loading-spinner {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        background: rgba(255, 255, 255, 0.8);
    }
    
    .spinner {
        border: 16px solid #f3f3f3;
        border-top: 16px solid #3498db;
        border-radius: 50%;
        width: 120px;
        height: 120px;
        animation: spin 2s linear infinite;
    }
    
    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }
  </style>
  