<script>
  import Info from './Info.svelte'

  let key
  let validated = true

  function handleSubmit(event) {
    event.preventDefault()
    if (key !== 'zf') {
      alert('回答错误')
      return
    }
    alert('回答正确')
    validated = true
    //TODO: 跳转个人介绍页面
  }
</script>

{#if !validated}
  <div class="background">
    <div class="box">
      <h1>四个大字</h1>
      <form on:submit={handleSubmit}>
        <input
          type="text"
          placeholder="请问我的名字是什么？"
          bind:value={key}
        />
        <button type="submit" disabled={!key}>确 定</button>
      </form>

      <footer>
        <p>Powerd by Svelte</p>
        <p>@Y80 - xxx</p>
      </footer>
    </div>
  </div>
{:else}
  <Info />
{/if}

<style lang="scss">
  .background {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(45deg, white, #9198e5, #e66465);
  }

  .box {
    box-sizing: border-box;
    margin-top: -5rem;
    padding: 1rem 2rem;
    width: 500px;
    border-radius: 6px;
    background: rgba(255, 255, 255, 0.6);

    backdrop-filter: blur(10px);
  }
  h1 {
    text-align: center;
  }

  input {
    width: 100%;
    border: none;
    border-bottom: 1px #999 solid;
    background: none;

    &:focus {
      outline: none;
    }
    &::placeholder {
      font-size: 12px;
    }
  }

  button {
    display: block;
    margin: 1rem auto;
    width: 100%;
    border: none;
    border-radius: 99px;
    background: linear-gradient(
    45deg,
    hsl(235, 100%, 60%),
    hsl(235, 100%, 53%)
    );
    color: white;
    line-height: 2rem;
    transition: all 200ms ease;

    &[disabled] {
      filter: grayscale(0.8) opacity(0.5);
      cursor: not-allowed;
    }
  }

  footer {
    color: #999;
    text-align: center;
    font-size: 12px;
    p {
      margin: 0;
    }
  }

  @media screen and (max-width: 500px) {
    .box {
      width: 90%;
    }
  }

</style>
