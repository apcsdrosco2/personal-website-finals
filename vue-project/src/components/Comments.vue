<template>
  <div class="comments-container">
    <h2>Leave a Comment</h2>
    <form @submit.prevent="submitComment">
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="name" required />
      
      <label for="comment">Comment:</label>
      <textarea id="comment" v-model="comment" required></textarea>
      
      <button type="submit">Submit</button>
    </form>
    
    <h2>Comments</h2>
    <ul>
      <li v-for="cmt in comments" :key="cmt.id">
        <strong>{{ cmt.name }}:</strong> {{ cmt.comment }}
        <br>
        <small>{{ new Date(cmt.created_at).toLocaleString() }}</small>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { createClient } from "@supabase/supabase-js";

const supabaseUrl = "https://rduihiqxzggscvyaafrm.supabase.co";
const supabaseKey = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InJkdWloaXF4emdnc2N2eWFhZnJtIiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImlhdCI6MTczODQ3MDQ0MywiZXhwIjoyMDU0MDQ2NDQzfQ.4BWkIeOf-wFpB6Mb6cZO2jDdzKWzL51STAYk_BVibZU";
const supabase = createClient(supabaseUrl, supabaseKey);

export default {
  setup() {
    const name = ref("");
    const comment = ref("");
    const comments = ref([]);

    const fetchComments = async () => {
      const { data, error } = await supabase
        .from("comments")
        .select("*")
        .order("created_at", { ascending: false });
      if (!error) comments.value = data;
    };

    const submitComment = async () => {
      if (!name.value || !comment.value) return;
      const { error } = await supabase
        .from("comments")
        .insert([{ name: name.value, comment: comment.value }]);
      if (!error) {
        name.value = "";
        comment.value = "";
        fetchComments();
      }
    };

    onMounted(fetchComments);
    return { name, comment, comments, submitComment };
  }
};
</script>

<style scoped>
.comments-container {
  max-width: 600px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #f9f9f9;
}
input, textarea {
  width: 100%;
  padding: 8px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
}
button {
  background: #007bff;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background: #0056b3;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  background: white;
  padding: 10px;
  margin: 5px 0;
  border-radius: 5px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}
</style>
