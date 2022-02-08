<template lang="html">
  <div class="container">
    <h2>{{title}}</h2>
    <p><i>This generates a new wallet address & mnemonic seed </i></p>
        <p><i>You can visit the Quenero websites to get more informations <br>
              Websites: <a target="_blank" href="https://quenero.tech/">Quenero.Tech</a> and
             <a target="_blank" href="https://docs.quenero.tech/">DOCS</a> <br>
             Explorer: <a target="_blank" href="https://explorer.quenero.tech/">Block Explorer</a>
         </i></p>

    <div class="btn-group btn-group-lg" role="group">
      <button type="button" v-on:click="createWallet" class="btn btn-success">Create Wallet</button>
    </div>
    <br><br>
    <div id="panel1" class="console panel panel-default" :class="displayClass">
      <div class="panel-heading">
        <h3 class="panel-title"> Public Address </h3>
      </div>
      <div class="panel-body">
        {{ public_addr }}
      </div>
    </div>
    <div id="panel2" class="console panel panel-default" :class="displayClass">
      <div class="panel-heading">
        <h3 class="panel-title"> Mnemonic seed </h3>
      </div>
      <div class="panel-body">
        {{ mnemonicString }}
      </div>
    </div>
    <hr>
    <i>
      Source code @  <a target="_blank" href="https://github.com/quenero/qmr-paper">Github.com-Paper</a>
    </i>
  </div>
</template>

<script>
const walletUtils = require('mymonero-core-js/monero_utils/monero_wallet_utils')

export default {
  data () {
    return {
      title: 'Quenero Paper',
      displayClass: 'is-hidden',
      mnemonicString: '',
      public_addr: ''
    }
  },
  methods: {
    createWallet: function () {
      const wallet = walletUtils.NewlyCreatedWallet('english')
      this.public_addr = wallet.keys.public_addr
      this.mnemonicString = wallet.mnemonicString
      this.displayClass = ''
    }
  }
}
</script>

<style lang="css">
  .panel-body {
    font-family: "Lucida Console", "Lucida Sans Typewriter", monaco, "Bitstream Vera Sans Mono", monospace;
    font-size: 12px;
    text-align: left;
    color: #2bf22b;
    background-color: #000;
  }
  .console {
    overflow-wrap: break-word;
    margin: auto;
    max-width: 720px
  }

  .is-hidden {
    visibility: hidden;
  }
</style>
