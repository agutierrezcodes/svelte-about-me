<script>
    export let image;  // Image URL prop
    export let title;  // Title prop
    export let description;  // Description prop
  </script>
  
  <style>
    .card {
      background-color: rgb(7, 7, 23);
      border: 1px solid rgb(161, 141, 236);
      border-radius: 10px;
      overflow: hidden;
      width: 300px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      margin: 20px;
      text-align: center;
      box-shadow: 6px 6px 8px 2px black;
    }
  
    .card img {
      width: 100%;
      height: auto;
      border-radius: 6px;
      box-shadow: 6px 6px 8px 2px black;
    }
  
    .card-content {
      padding: 15px;
    }
  
    .card-title {
      font-size: 1.5em;
      color: rgb(211, 210, 210);
      margin: 0 0 10px 0;
    }
  
    .card-description {
      font-size: 1em;
      color: rgb(211, 210, 210);
      margin: 0;
    }
  </style>
  
  <div class="card">
    <img src={image} alt={title} />
    <div class="card-content">
      <h2 class="card-title">{title}</h2>
      <p class="card-description">{description}</p>
    </div>
  </div>