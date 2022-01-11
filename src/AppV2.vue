<template>
  <h3>Test using "global store" component</h3>

  <wallet-modal-provider>
    <wallet-multi-button/>
  </wallet-modal-provider>
</template>

<script lang="ts">
  import {defineComponent} from 'vue';
  import {Wallet} from "@solana/wallet-adapter-base";
  import {initWallet} from "@solana/wallet-adapter-vue";
  import {getPhantomWallet, getSolflareWallet} from "@solana/wallet-adapter-wallets";
  import {WalletModalProvider, WalletMultiButton} from "@solana/wallet-adapter-vue-ui";

  export default defineComponent({
    name: 'AppV2',
    components: {
      WalletMultiButton,
      WalletModalProvider,
    },
    setup() {
      const wallets: Wallet[] = [
        getPhantomWallet(),
        getSolflareWallet(),
      ];

      initWallet({
        wallets,
        autoConnect: true,
      });

      return {wallets};
    }
  });
</script>
