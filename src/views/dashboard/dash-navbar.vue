<template>
  <!--Top Navbar-->
  <div class="container-fluid no-gutters">
    <div class="row">
      <div class="col-lg-12 p-0">
        <div
          class="header_iner d-flex justify-content-between align-items-center"
        >
          <!--Hamburger-->
          <div class="line_icon open_miniSide d-lg-block">
            <img src="@/assets/img/dashboard-img/line_img.png" />
          </div>
          <!--Search Bar-->
          <div class="serach_field-area d-flex align-items-center">
            <!-- <div class="search_inner">
                            <form action="#">
                                <div class="search_field">
                                    <input type="text" placeholder="Search">
                                </div>
                                <button type="submit"> <img src="@/assets/img/icon/icon_search.svg"> </button>
                            </form>
                        </div> -->
          </div>
          <div
            class="header_right d-flex justify-content-between align-items-center"
          >
            <!--Notification-->
            <div class="header_notification_warp d-flex align-items-center">
              <li>
                <router-link
                  class="bell_notification_clicker"
                  to="/dashboard/all-notifications"
                >
                  <img src="@/assets/img/icon/bell.svg" alt="" />
                  <span :class="notifications && 'ifNotification'">{{
                    notifications
                  }}</span>
                </router-link>
                <!-- <div class="Menu_NOtification_Wrap">
                  <div class="notification_Header">
                    <h4>Notifications</h4>
                  </div>
                  <div class="Notification_body">
                    <div class="single_notify d-flex align-items-center">
                      <div class="notify_thumb">
                        <a href="#"
                          ><img src="@/assets/img/customers/1.png" alt=""
                        /></a>
                      </div>
                      <div class="notify_content">
                        <a href="#">
                          <h5>Cool Marketing</h5>
                        </a>
                        <p>Lorem ipsum dolor sit amet</p>
                      </div>
                    </div>
                    <div class="single_notify d-flex align-items-center">
                      <div class="notify_thumb">
                        <a href="#"
                          ><img src="@/assets/img/customers/1.png" alt=""
                        /></a>
                      </div>
                      <div class="notify_content">
                        <a href="#">
                          <h5>Awesome packages</h5>
                        </a>
                        <p>Lorem ipsum dolor sit amet</p>
                      </div>
                    </div>
                    <div class="single_notify d-flex align-items-center">
                      <div class="notify_thumb">
                        <a href="#"
                          ><img src="@/assets/img/customers/1.png" alt=""
                        /></a>
                      </div>
                      <div class="notify_content">
                        <a href="#">
                          <h5>what a packages</h5>
                        </a>
                        <p>Lorem ipsum dolor sit amet</p>
                      </div>
                    </div>
                    <div class="single_notify d-flex align-items-center">
                      <div class="notify_thumb">
                        <a href="#"
                          ><img src="@/assets/img/customers/1.png" alt=""
                        /></a>
                      </div>
                      <div class="notify_content">
                        <a href="#">
                          <h5>Cool Marketing</h5>
                        </a>
                        <p>Lorem ipsum dolor sit amet</p>
                      </div>
                    </div>
                    <div class="single_notify d-flex align-items-center">
                      <div class="notify_thumb">
                        <a href="#"
                          ><img src="@/assets/img/customers/1.png" alt=""
                        /></a>
                      </div>
                      <div class="notify_content">
                        <a href="#">
                          <h5>Awesome packages</h5>
                        </a>
                        <p>Lorem ipsum dolor sit amet</p>
                      </div>
                    </div>
                    <div class="single_notify d-flex align-items-center">
                      <div class="notify_thumb">
                        <a href="#"
                          ><img src="@/assets/img/customers/1.png" alt=""
                        /></a>
                      </div>
                      <div class="notify_content">
                        <a href="#">
                          <h5>what a packages</h5>
                        </a>
                        <p>Lorem ipsum dolor sit amet</p>
                      </div>
                    </div>
                  </div>
                  <div class="nofity_footer">
                    <div class="submit_button text-center pt_20">
                      <router-link
                        to="/dashboard/all-notifications"
                        class="btn_1"
                        >See More</router-link
                      >
                    </div>
                  </div>
                </div> -->
              </li>
            </div>
            <!--Profile-->
            <div class="profile_info">
              <img src="@/assets/img/client_img.png" alt="#" />
              Hi, {{ user.firstname }} <i class="bi bi-caret-down"></i>
              <div class="profile_info_iner">
                <div class="profile_author_name">
                  <p style="font-size: 15px;">Admin Account</p>
                  <h5>{{ user.firstname }} {{ user.lastname[0] }}.</h5>
                  <p style="margin-top: -10px;font-size: 12px;font-weight: 500;">Admintrator</p>
                </div>
                <div class="profile_info_details">
                  
                  <router-link to="/admin-dashboard/home">
                    <img src="@/assets/img/menu-icon/dashboard.png" style="border: 0;border-radius: 0;margin-right: 10px;"> Dashboard
                  </router-link>
                  <router-link to="/admin-dashboard/profile" style="margin-left: -22px;"
                    ><i style="margin-right: 8px;font-size: 20px;" class="bi bi-person-circle"></i> My Profile</router-link
                  >
                  <a @click.prevent="logOut">
                    <img src="@/assets/img/menu-icon/logout.png" style="border: 0;border-radius: 0;margin-right: 10px; width: 15px;"  /> Log Out
                  </a>
                  
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped src="@/assets/vendors/themefy_icon/themify-icons.css"></style>
<style scoped src="@/assets/vendors/niceselect/css/nice-select.css"></style>
<style scoped src="@/assets/css/style.css"></style>
<script>
export default {
  name: "dashboard",
  computed: {
    currentUser() {
      const user = JSON.parse(localStorage.getItem("user"));
      // console.log(user);
      if (user) {
        // console.log(user);
        return user;
      }
    },
  },
  data() {
    return {
      user: JSON.parse(localStorage.getItem("user")),
      notifications: 0,
    };
  },

  methods: {
    logOut() {
      this.$store.dispatch("auth/logout");
      this.$router.push("/admin/login");
    },
    async getAllNotifications() {
      const res = await fetch(
        "https://producemart.herokuapp.com/getAdminNotifications",
        {
          method: "GET",
          headers: {
            Authorization: this.user.token,
          },
        }
      );
      const { data } = await res.json();
      this.notifications = data.filter((prod) => !prod.read).length;

      //   console.log(this.notifications);
    },
  },
  mounted() {
    this.getAllNotifications();
    if (!this.currentUser) {
      this.$router.push("/admin/login");
    }
    window.scrollTo(0, 0);

    let externalScriptJquery = document.createElement("script");
    let externalScriptMetisMenu = document.createElement("script");
    let externalScriptCustom = document.createElement("script");

    externalScriptJquery.setAttribute(
      "src",
      "https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"
    );
    externalScriptMetisMenu.setAttribute(
      "src",
      "https://cdn.statically.io/gh/NathTimi/Mart-script/main/metisMenu.js"
    );
    externalScriptCustom.setAttribute(
      "src",
      "https://cdn.statically.io/gh/NathTimi/Mart-script/main/custom.js"
    );

    document.head.appendChild(externalScriptJquery);
    document.head.appendChild(externalScriptMetisMenu);
    document.head.appendChild(externalScriptCustom);
  },
};
</script>
