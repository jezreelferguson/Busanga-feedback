<template>
  <div class="feedback-wrap">
    <form class="feedback-card" novalidate>
      <h2 class="title">Send Feedback</h2>

      <label class="field">
        <span class="label-text">Feedback Title</span>
        <input
          type="text"
          class="input"
          placeholder="Briefly describe your feedback"
          maxlength="100"
          required
        />
        <small class="help">Max 100 characters</small>
      </label>

      <label class="field">
        <span class="label-text">Feedback</span>
        <textarea
          class="textarea"
          placeholder="Tell us what you'd like improved, or what's great"
          rows="6"
          maxlength="1000"
          required
        ></textarea>
        <div class="meta">
          <small class="help">Max 1000 characters</small>
          <small class="charcount">0 / 1000</small>
        </div>
      </label>

      <div class="actions">
        <button type="submit" class="btn">
          Submit
        </button>
      </div>

      <transition name="fade">
        <div class="success">
          Thank you — your feedback has been submitted.
        </div>
      </transition>
    </form>
  </div>
</template>

<style scoped>
.feedback-wrap {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  background: linear-gradient(180deg, #f6fbff 0%, #ffffff 100%);
}
.feedback-card {
  width: 100%;
  max-width: 720px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 8px 30px rgba(23, 43, 77, 0.08);
  padding: 1.6rem;
  border: 1px solid rgba(18, 38, 63, 0.04);
}
.title {
  font-size: 1.35rem;
  font-weight: 700;
  color: #12263f;
  margin-bottom: 1rem;
}
.field {
  margin-bottom: 1rem;
}
.label-text {
  display: block;
  margin-bottom: 0.4rem;
  font-size: 0.95rem;
  color: #334455;
}
.input, .textarea {
  width: 100%;
  padding: 0.75rem 0.85rem;
  border-radius: 8px;
  border: 1px solid #e6eef6;
  font-size: 0.97rem;
  color: #0f1724;
  outline: none;
  transition: 0.15s;
}
.input:focus, .textarea:focus {
  border-color: #8aa7ff;
  box-shadow: 0 6px 18px rgba(13, 70, 161, 0.06);
}
.help {
  font-size: 0.82rem;
  color: #74839a;
}
.meta {
  display: flex;
  justify-content: space-between;
  margin-top: 0.4rem;
}
.charcount {
  font-size: 0.82rem;
  color: #94a3b8;
}
.actions {
  display: flex;
  justify-content: flex-end;
}
.btn {
  background: linear-gradient(90deg, #5063f2 0%, #2ea6ff 100%);
  color: white;
  border: none;
  padding: 0.66rem 1.05rem;
  border-radius: 10px;
  font-weight: 600;
  cursor: pointer;
  box-shadow: 0 6px 18px rgba(46, 166, 255, 0.18);
  transition: 0.12s;
}
.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
.success {
  margin-top: 0.9rem;
  padding: 0.6rem 0.9rem;
  background: rgba(34,197,94,0.12);
  border: 1px solid rgba(34,197,94,0.12);
  color: #064e3b;
  border-radius: 8px;
  font-weight: 600;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 240ms ease, transform 240ms ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateY(-6px);
}
@media (max-width: 520px) {
  .feedback-card { padding: 1rem; }
  .title { font-size: 1.15rem; }
}
</style>
