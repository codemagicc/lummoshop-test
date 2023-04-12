<template>
  <div class="container W-500">
    <div class="row">
      <top-alert v-show="showAlert"/>
    </div>

    <div :class="fixedHeader && 'navbar-fixed'">
      <div class="row align-center navbar">
        <div class="col-sm-1" v-on:click="navLink = !navLink">
          <header-icon />
        </div>
        <div class="col-sm-9">
          <div class="header-store-title">
            <img alt="Catalog" src="/icons/store.png" />
            <div class="px-3">Catalog</div>
          </div>
        </div>
        <div class="col-sm-1" v-on:click="searchBox = !searchBox">
          <search-icon />
        </div>
        <div class="col-sm-1">
          <shopping-icon />
        </div>
      </div>
    </div>

    <div class="nav-content" :class="navLink && 'display-nav'">
      <div class="nav-orders mt-3">
        <div class="row">
          <div class="col-sm-1">
            <profile-icon />
          </div>
          <div class="col-sm-10 order-detail">
            <h6 class="mb-0">Pesanan Saya</h6>
            <p>Semua pesananmu di online shop LummoSHOP dapat dilihat di sini.</p>
          </div>
          <div class="col-sm-1">
            <right-arrow-icon />
          </div>
        </div>
      </div>

      <div class="nav-store mt-4">
        <div class="row">
          <div class="col-sm-1">
            <store-icon />
          </div>
          <div class="col-sm-10 store-info">
            <p>Info Toko</p>
          </div>
          <div class="col-sm-1"></div>
        </div>

        <div class="row">
          <div class="col-sm-1">
            <side-bar-nav-icon />
          </div>
        </div>

        <div class="row">
          <div class="col-sm-1">
            <side-bar-icon />
          </div>
          <div class="col-sm-11">
            <div class="days-info">
              <div class="days-common days-left">Senin</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
            <div class="days-info">
              <div class="days-common days-left">Selasa</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
            <div class="days-info">
              <div class="days-common days-left">Rabu</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
            <div class="days-info">
              <div class="days-common days-left">Kamis</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
            <div class="days-info">
              <div class="days-common days-left">Jumat</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
            <div class="days-info">
              <div class="days-common days-left">Sabtu</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
            <div class="days-info">
              <div class="days-common days-left">Minggu</div>
              <div class="days-common days-right">Buka 24 Jam</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="inner-data" v-if="!navLink">
      <div class="row">
        <div class="col-md-12 store-body text-center">
          <div class="col-md-12 shopbag">
            <img src="/icons/shopbag.png" alt="shopbag" />
          </div>

          <div class="col-md-12">
            <div class="no-products text-center">Belum ada produk di toko ini, cek lagi nanti!</div>
          </div>
        </div>
      </div>

      <div class="row payment-methods text-center">
        <div class="col-md-12">
          <p class="payment-text">Metode Pembayaran Terpercaya</p>
          <p class="payment-desc">
            Bayar dengan metode pembayaran pilihan kamu. Dijamin 100% aman!
          </p>
        </div>

        <div class="col-md-12">
          <payment-methods :icons="paymentIcons" className="payment-icon" />
        </div>
        <div class="col-md-12">
          <p class="delivery-text">Pengiriman Cepat dan Aman</p>
          <p class="delivery-desc">
            Pengiriman produk aman dan cepat dengan memilih mitra kurir terpercaya kami.
          </p>
        </div>

        <div class="col-md-12">
          <delivery-methods :icons="deliveryIcon" className="delivery-icon"/>
        </div>
      </div>

      <div class="row copyright text-center">
        <p class="mb-0">&copy; 2023 Catalog</p>
      </div>

      <div class="row follow-sm">
        <div class="col-sm-6 text-left">
          <p class="mb-0 pt-2">FOLLOW DI SOSIAL MEDIA</p>
        </div>
        <div class="col-sm-6 text-right">
          <button class="sm-icon-outer"><img src="/icons/Facebook.svg" class="sm-icon" /></button
          ><button class="sm-icon-outer"><img src="/icons/Instagram.svg" class="sm-icon" /></button
          ><button class="sm-icon-outer">
            <img src="/icons/WhatsappGreenBG.svg" class="sm-icon" />
          </button>
        </div>
      </div>

      <div class="row safe-info">
        <a href="https://tokko.app.link/uGWKUMXpWab" target="_blank" class="">
          <div class="safe-info-color">
            Dibuat dengan<img src="/icons/logo-created-with-lummo.png" alt="Lummo" class="" />
          </div>
        </a>
      </div>

      <div class="row safe-info-footer">
        <div class="col-sm-1 pl-26">
          <safe-info-icon />
        </div>
        <div class="col-sm-11">
          <p class="mb-0">
            Platform terpercaya untuk membantu kamu berbelanja. Semua infomu terjamin aman.
          </p>
        </div>
      </div>
    </div>

    <a href="https://wa.me/+6283824253182" class="whats-app"><whats-app-icon /></a>

    <div class="row search-box" v-if="searchBox">
      <div class="col-sm-2" v-on:click="searchBox = !searchBox">
        <CrossIcon />
      </div>
      <div class="col-sm-10">
        <div class="form-group has-search">
          <span class="form-control-feedback">
            <search-icon />
          </span>
          <input type="text" class="form-control search" placeholder="Search" />
        </div>
      </div>
    </div>
  </div>

  <!-- <RouterView /> -->
</template>
<script>
import SearchIcon from '../components/icons/SearchIcon.vue'
import CrossIcon from '../components/icons/CrossIcon.vue'
import WhatsAppIcon from '../components/icons/WhatsAppIcon.vue'
import SafeInfoIcon from '../components/icons/SafeInfoIcon.vue'
import SideBarIcon from '../components/icons/SideBarIcon.vue'
import SideBarNavIcon from '../components/icons/SideBarNavIcon.vue'
import StoreIcon from '../components/icons/StoreIcon.vue'
import HeaderIcon from '../components/icons/HeaderIcon.vue'
import ProfileIcon from '../components/icons/ProfileIcon.vue'
import RightArrowIcon from '../components/icons/RightArrowIcon.vue'
import ShoppingIcon from '../components/icons/ShoppingIcon.vue'
import PaymentMethods from '../components/PaymentMethods.vue'
import DeliveryMethods from '../components/DeliveryMethods.vue'
import TopAlert from '../components/TopAlert.vue'

export default {
  data() {
    return {
      navLink: false,
      showAlert: true,
      fixedHeader: false,
      searchBox: false,
      paymentIcons: [
        { img: '/icons/BankBri.png', alt: 'Bri' },
        { img: '/icons/Bni.png', alt: 'Bni' },
        { img: '/icons/Mandiri.png', alt: 'Mandiri' },
        { img: '/icons/Permata.png', alt: 'Permata' },
        { img: '/icons/Cimb.png', alt: 'Cimb' },
        { img: '/icons/DanaBrand.svg', alt: 'DanaBrand' },
        { img: '/icons/ShopeePay.png', alt: 'ShopeePay' },
        { img: '/icons/OvoBrand.png', alt: 'OvoBrand' },
        { img: '/icons/Linkaja.png', alt: 'Linkaja' }
      ],
      deliveryIcon: [
        { img: '/icons/JT.svg', alt: 'JNT' },
        { img: '/icons/Ninja.svg', alt: 'Ninja' },
        { img: '/icons/Paxel.png', alt: 'Paxel' },
        { img: '/icons/Sicepat.png', alt: 'Sicepat' },
        { img: '/icons/GoSend.svg', alt: 'GoSend' },
        { img: '/icons/GrabExpress.svg', alt: 'GrabExpress' },
        { img: '/icons/Borzo.svg', alt: 'Borzo' },
        { img: '/icons/LalaMove.png', alt: 'LalaMove' }
      ]
    }
  },
  components: {
    SearchIcon,
    CrossIcon,
    WhatsAppIcon,
    SafeInfoIcon,
    SideBarIcon,
    SideBarNavIcon,
    StoreIcon,
    HeaderIcon,
    ProfileIcon,
    RightArrowIcon,
    ShoppingIcon,
    PaymentMethods,
    DeliveryMethods,
    TopAlert,
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      const scrollPosition = window.scrollY || document.documentElement.scrollTop

      this.showAlert = scrollPosition <= 0
      this.fixedHeader = scrollPosition >= 10
    }
  }
}
</script>
<style scoped></style>
