<template>
  <f-asset-select v-model="asset" :assets="assets"></f-asset-select>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import assets from "@/assets/assets.json";

@Component
class AssetSelect extends Vue {
  asset = null;

  get assets() {
    return assets.map((asset) => {
      const chainAsset = assets.find((a) => a.asset_id === asset.chain_id);
      return {
        id: asset.asset_id,
        symbol: asset.symbol,
        name: asset.name,
        logo: asset.icon_url,
        label: asset.label,
        chainLogo: chainAsset && chainAsset.icon_url,
      };
    });
  }
}
export default AssetSelect;
</script>
