<template>
  <h3>Test using wallet-provider component</h3>

  <wallet-provider :auto-connect="true" :wallets="wallets">
    <wallet-modal-provider>
      <wallet-multi-button/>
    </wallet-modal-provider>
  </wallet-provider>
</template>

<script lang="ts">
  import {defineComponent} from 'vue';
  import {Wallet} from "@solana/wallet-adapter-base";
  import {WalletProvider} from "@solana/wallet-adapter-vue";
  import {getPhantomWallet, getSolflareWallet} from "@solana/wallet-adapter-wallets";
  import {WalletModalProvider, WalletMultiButton} from "@solana/wallet-adapter-vue-ui";

  export default defineComponent({
    name: 'App',
    components: {
      WalletMultiButton,
      WalletModalProvider,
      WalletProvider,
    },
    setup() {
      const wallets: Wallet[] = [
        getPhantomWallet(),
        getSolflareWallet(),
      ];

      return {wallets};
    }
  });
</script>
