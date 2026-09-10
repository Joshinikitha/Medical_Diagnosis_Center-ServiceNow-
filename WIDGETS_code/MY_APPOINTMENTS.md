# **MY\_APPOINTMENTS**

#### **HTML**

<div class="my-appts">

<!-- HEADER -->

&#x20; <div class="appts-header">

&#x20;   <div class="header-left">

&#x20;     <h1 class="header-title">📋 My Appointments</h1>

&#x20;     <p class="header-sub">Track all your booked diagnostic tests in one place.</p>

&#x20;   </div>

&#x20;   <div class="header-right">

&#x20;     <button class="btn-book-new" ng-click="c.bookNew()">

&#x20;       <i class="fa fa-plus"></i> Book New Test

&#x20;     </button>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- STATS BAR -->

&#x20; <div class="stats-bar">

&#x20;   <div class="stat-card" ng-repeat="stat in c.stats">

&#x20;     <span class="stat-icon">{{stat.icon}}</span>

&#x20;     <div class="stat-info">

&#x20;       <span class="stat-val">{{stat.count}}</span>

&#x20;       <span class="stat-name">{{stat.label}}</span>

&#x20;     </div>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- FILTER TABS -->

&#x20; <div class="filter-tabs">

&#x20;   <button

&#x20;     class="filter-tab"

&#x20;     ng-repeat="tab in c.tabs"

&#x20;     ng-class="{'active': c.activeTab === tab.key}"

&#x20;     ng-click="c.setTab(tab.key)"

&#x20;   >

&#x20;     {{tab.label}}

&#x20;     <span class="tab-count" ng-if="tab.count > 0">{{tab.count}}</span>

&#x20;   </button>

&#x20; </div>



&#x20; <!-- SEARCH + SORT -->

&#x20; <div class="list-controls">

&#x20;   <div class="search-mini-wrap">

&#x20;     <i class="fa fa-search"></i>

&#x20;     <input

&#x20;       type="text"

&#x20;       placeholder="Search appointments..."

&#x20;       ng-model="c.searchQuery"

&#x20;       ng-change="c.filterAppointments()"

&#x20;       class="search-mini"

&#x20;     />

&#x20;   </div>

&#x20;   <select ng-model="c.sortBy" ng-change="c.sortAppointments()" class="sort-mini">

&#x20;     <option value="date\_desc">Newest First</option>

&#x20;     <option value="date\_asc">Oldest First</option>

&#x20;     <option value="status">By Status</option>

&#x20;   </select>

&#x20; </div>



&#x20; <!-- LOADING -->

&#x20; <div class="loading-center" ng-if="c.loading">

&#x20;   <div class="spinner-ring"></div>

&#x20;   <p>Loading your appointments...</p>

&#x20; </div>



&#x20; <!-- EMPTY STATE -->

&#x20; <div class="empty-appts" ng-if="!c.loading \&\& c.filteredAppointments.length === 0">

&#x20;   <div class="empty-emoji">

&#x20; <i class="fa fa-calendar-o"></i>

</div>

&#x20;   <h3>No appointments found</h3>

&#x20;   <p ng-if="c.activeTab !== 'all'">No {{c.activeTab}} appointments yet.</p>

&#x20;   <p ng-if="c.activeTab === 'all'">You haven't booked any tests yet.</p>

&#x20;   <button class="btn-book-first" ng-click="c.bookNew()">Book Your First Test</button>

&#x20; </div>



&#x20; <!-- APPOINTMENTS LIST -->

&#x20; <div class="appts-list" ng-if="!c.loading \&\& c.filteredAppointments.length > 0">

&#x20;   <div

&#x20;     class="appt-card"

&#x20;     ng-repeat="appt in c.filteredAppointments"

&#x20;     ng-class="'appt-' + appt.status"

&#x20;   >



&#x20;     <!-- LEFT ACCENT BAR -->

&#x20;     <div class="appt-accent-bar" ng-style="{'background': c.getStatusColor(appt.status)}"></div>



&#x20;     <!-- CARD CONTENT -->

&#x20;     <div class="appt-content">



&#x20;       <!-- TOP ROW -->

&#x20;       <div class="appt-top">

&#x20;         <div class="appt-title-group">

&#x20;           <span class="appt-icon">{{c.getCategoryIcon(appt.test\_category)}}</span>

&#x20;           <div>

&#x20;             <h3 class="appt-test-name">{{appt.test\_name}}</h3>

&#x20;             <span class="appt-number">{{appt.appointment\_number}}</span>

&#x20;           </div>

&#x20;         </div>

&#x20;         <div class="appt-status-wrap">

&#x20;           <span

&#x20;             class="status-pill"

&#x20;             ng-style="{'background': c.getStatusBg(appt.status), 'color': c.getStatusColor(appt.status)}"

&#x20;           >

&#x20;             {{c.getStatusIcon(appt.status)}} {{c.getStatusLabel(appt.status)}}

&#x20;           </span>

&#x20;           <span

&#x20;             class="approval-pill"

&#x20;             ng-if="appt.approval\_status"

&#x20;             ng-class="'approval-' + appt.approval\_status"

&#x20;           >

&#x20;             {{c.getApprovalLabel(appt.approval\_status)}}

&#x20;           </span>

&#x20;         </div>

&#x20;       </div>



&#x20;       <!-- META ROW -->

&#x20;       <div class="appt-meta">

&#x20;         <div class="meta-chip">

&#x20;           <i class="fa fa-calendar"></i>

&#x20;           <span>{{appt.scheduled\_date\_display}}</span>

&#x20;         </div>

&#x20;         <div class="meta-chip">

&#x20;           <i class="fa fa-clock-o"></i>

&#x20;           <span>{{appt.slot\_time || 'N/A'}}</span>

&#x20;         </div>

&#x20;         <div class="meta-chip">

&#x20;           <i class="fa fa-tag"></i>

&#x20;           <span>{{appt.test\_category || 'General'}}</span>

&#x20;         </div>

&#x20;         <div class="meta-chip" ng-if="appt.total\_amount">

&#x20;           <i class="fa fa-dollar"></i>

&#x20;           <span>${{appt.total\_amount | number:2}}</span>

&#x20;         </div>

&#x20;       </div>



&#x20;       <!-- PAYMENT + APPROVAL STATUS -->

&#x20;       <div class="appt-info-row">

&#x20;         <div class="info-badge" ng-class="'pay-' + appt.payment\_status">

&#x20;           <i class="fa fa-credit-card"></i>

&#x20;           Payment: <strong>{{c.getPaymentLabel(appt.payment\_status)}}</strong>

&#x20;         </div>

&#x20;         <div class="info-badge approval-info" ng-if="appt.approved\_by\_name">

&#x20;           <i class="fa fa-user-check"></i>

&#x20;           Approved by: <strong>{{appt.approved\_by\_name}}</strong>

&#x20;         </div>

&#x20;         <div class="info-badge conf-badge" ng-if="appt.confirmation\_sent">

&#x20;           <i class="fa fa-envelope-o"></i> Confirmation Sent

&#x20;         </div>

&#x20;       </div>



&#x20;       <!-- NOTES -->

&#x20;       <div class="appt-notes" ng-if="appt.notes">

&#x20;         <i class="fa fa-sticky-note-o"></i> <em>{{appt.notes}}</em>

&#x20;       </div>



&#x20;       <!-- REJECTION REASON -->

&#x20;       <div class="rejection-banner" ng-if="appt.rejection\_reason">

&#x20;         <i class="fa fa-exclamation-circle"></i>

&#x20;         <div>

&#x20;           <strong>Rejection Reason:</strong>

&#x20;           <span>{{appt.rejection\_reason}}</span>

&#x20;         </div>

&#x20;       </div>



&#x20;       <!-- ACTIONS -->

&#x20;       <div class="appt-actions">

&#x20;         <button

&#x20;           class="appt-action-btn btn-view"

&#x20;           ng-click="c.viewDetails(appt)"

&#x20;         >

&#x20;           <i class="fa fa-eye"></i> View Details

&#x20;         </button>

&#x20;         <button

&#x20;           class="appt-action-btn btn-cancel"

&#x20;           ng-if="c.canCancel(appt)"

&#x20;           ng-click="c.cancelAppointment(appt)"

&#x20;         >

&#x20;           <i class="fa fa-times"></i> Cancel

&#x20;         </button>

&#x20;         <button

&#x20;           class="appt-action-btn btn-report"

&#x20;           ng-if="appt.has\_report"

&#x20;           ng-click="c.viewReport(appt)"

&#x20;         >

&#x20;           <i class="fa fa-file-text"></i> View Report

&#x20;         </button>

&#x20;         <span class="date-chip">

&#x20;           Booked: {{appt.created\_on\_display}}

&#x20;         </span>

&#x20;       </div>



&#x20;     </div>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- DETAIL MODAL -->

&#x20; <div class="modal-overlay" ng-if="c.showModal" ng-click="c.closeModal()">

&#x20;   <div class="modal-box" ng-click="$event.stopPropagation()">

&#x20;     <div class="modal-header">

&#x20;       <h3>Appointment Details</h3>

&#x20;       <button class="modal-close" ng-click="c.closeModal()">✕</button>

&#x20;     </div>

&#x20;     <div class="modal-body" ng-if="c.selectedAppt">

&#x20;       <div class="detail-grid">

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Appointment #</span>

&#x20;           <span class="detail-val mono">{{c.selectedAppt.appointment\_number}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Status</span>

&#x20;           <span class="detail-val">

&#x20;             <span class="status-pill" ng-style="{'background': c.getStatusBg(c.selectedAppt.status), 'color': c.getStatusColor(c.selectedAppt.status)}">

&#x20;               {{c.getStatusLabel(c.selectedAppt.status)}}

&#x20;             </span>

&#x20;           </span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Test</span>

&#x20;           <span class="detail-val">{{c.selectedAppt.test\_name}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Category</span>

&#x20;           <span class="detail-val">{{c.selectedAppt.test\_category}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Scheduled Date</span>

&#x20;           <span class="detail-val">{{c.selectedAppt.scheduled\_date\_display}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Time Slot</span>

&#x20;           <span class="detail-val">{{c.selectedAppt.slot\_time}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Total Amount</span>

&#x20;           <span class="detail-val paid-green">${{c.selectedAppt.total\_amount | number:2}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Payment Status</span>

&#x20;           <span class="detail-val">{{c.getPaymentLabel(c.selectedAppt.payment\_status)}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item">

&#x20;           <span class="detail-key">Approval Status</span>

&#x20;           <span class="detail-val">{{c.getApprovalLabel(c.selectedAppt.approval\_status)}}</span>

&#x20;         </div>

&#x20;         <div class="detail-item full">

&#x20;           <span class="detail-key">Notes</span>

&#x20;           <span class="detail-val">{{c.selectedAppt.notes || 'None'}}</span>

&#x20;         </div>

&#x20;       </div>

&#x20;     </div>

&#x20;     <div class="modal-footer">

&#x20;       <button class="btn-close-modal" ng-click="c.closeModal()">Close</button>

&#x20;     </div>

&#x20;   </div>

&#x20; </div>

</div>





#### **CSS**

/\* =========================================================

&#x20;  MEDICA — APPOINTMENTS

&#x20;  Clean clinical UI

&#x20;  ========================================================= \*/



.my-appts {

&#x20; --navy: #102a43;

&#x20; --blue: #1769aa;

&#x20; --blue-soft: #eaf4fb;

&#x20; --cyan: #1597b8;



&#x20; --green: #16835b;

&#x20; --green-bg: #eaf7f1;



&#x20; --amber: #a66a00;

&#x20; --amber-bg: #fff6df;



&#x20; --red: #c24141;

&#x20; --red-bg: #fff0f0;



&#x20; --text: #243b53;

&#x20; --text-light: #627d98;

&#x20; --muted: #829ab1;



&#x20; --border: #d9e2ec;

&#x20; --border-light: #e9eef3;



&#x20; --page: #f5f8fb;

&#x20; --white: #ffffff;



&#x20; font-family: "Segoe UI", Arial, sans-serif;

&#x20; background: var(--page);

&#x20; color: var(--text);

&#x20; min-height: 100vh;

&#x20; padding-bottom: 60px;



&#x20; /\* Prevent animation overflow \*/

&#x20; overflow: hidden;

}





/\* =========================================================

&#x20;  HEADER

&#x20;  ========================================================= \*/



.appts-header {

&#x20; position: relative;



&#x20; display: flex;

&#x20; justify-content: space-between;

&#x20; align-items: center;



&#x20; padding: 42px 48px 62px;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     115deg,

&#x20;     #102a43 0%,

&#x20;     #123f63 55%,

&#x20;     #155d7c 100%

&#x20;   );



&#x20; border-radius: 0 0 34px 34px;



&#x20; overflow: hidden;



&#x20; animation: headerEnter .55s ease-out both;

}





/\* subtle background shape \*/



.appts-header::after {

&#x20; content: "";



&#x20; position: absolute;



&#x20; width: 320px;

&#x20; height: 320px;



&#x20; right: -100px;

&#x20; top: -180px;



&#x20; border-radius: 50%;



&#x20; border: 1px solid rgba(255,255,255,.08);



&#x20; box-shadow:

&#x20;   0 0 0 55px rgba(255,255,255,.025),

&#x20;   0 0 0 110px rgba(255,255,255,.018);



&#x20; pointer-events: none;

}





.appts-header::before {

&#x20; content: "";



&#x20; position: absolute;



&#x20; width: 8px;

&#x20; height: 8px;



&#x20; right: 31%;

&#x20; bottom: 28px;



&#x20; border-radius: 50%;



&#x20; background: rgba(255,255,255,.25);



&#x20; box-shadow:

&#x20;   80px -45px 0 rgba(255,255,255,.12),

&#x20;   155px 10px 0 rgba(255,255,255,.08);

}





@keyframes headerEnter {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(-12px);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0);

&#x20; }



}





.header-left {

&#x20; position: relative;

&#x20; z-index: 2;

}





.header-title {

&#x20; margin: 0 0 9px;



&#x20; color: #ffffff;



&#x20; font-size: 31px;

&#x20; line-height: 1.2;



&#x20; font-weight: 700;



&#x20; letter-spacing: -.6px;

}





.header-sub {

&#x20; margin: 0;



&#x20; color: #b8cee0;



&#x20; font-size: 14px;



&#x20; line-height: 1.5;

}





.header-right {

&#x20; position: relative;

&#x20; z-index: 2;

}





/\* =========================================================

&#x20;  BOOK BUTTON

&#x20;  ========================================================= \*/



.btn-book-new {



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 9px;



&#x20; padding: 11px 19px;



&#x20; border: 1px solid rgba(255,255,255,.14);



&#x20; border-radius: 9px;



&#x20; background: #ffffff;



&#x20; color: var(--navy);



&#x20; font-size: 13px;



&#x20; font-weight: 700;



&#x20; cursor: pointer;



&#x20; box-shadow:

&#x20;   0 5px 16px rgba(0,0,0,.13);



&#x20; transition:

&#x20;   transform .25s ease,

&#x20;   box-shadow .25s ease,

&#x20;   background .25s ease;

}





.btn-book-new:hover {



&#x20; transform: translateY(-2px);



&#x20; background: #f7fbfe;



&#x20; box-shadow:

&#x20;   0 9px 22px rgba(0,0,0,.18);

}





.btn-book-new:active {



&#x20; transform: translateY(0);

}





/\* =========================================================

&#x20;  STATS

&#x20;  ========================================================= \*/



.stats-bar {



&#x20; position: relative;



&#x20; z-index: 5;



&#x20; display: grid;



&#x20; grid-template-columns:

&#x20;   repeat(

&#x20;     auto-fit,

&#x20;     minmax(170px, 1fr)

&#x20;   );



&#x20; gap: 14px;



&#x20; max-width: 1180px;



&#x20; margin: -30px auto 0;



&#x20; padding: 0 24px;

}





.stat-card {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 13px;



&#x20; min-height: 74px;



&#x20; padding: 13px 17px;



&#x20; background: var(--white);



&#x20; border: 1px solid var(--border-light);



&#x20; border-radius: 12px;



&#x20; box-shadow:

&#x20;   0 5px 20px rgba(36,59,83,.07);



&#x20; animation: statEnter .5s ease-out both;



&#x20; transition:

&#x20;   transform .25s ease,

&#x20;   box-shadow .25s ease,

&#x20;   border-color .25s ease;

}





.stat-card:nth-child(2) {

&#x20; animation-delay: .05s;

}



.stat-card:nth-child(3) {

&#x20; animation-delay: .1s;

}



.stat-card:nth-child(4) {

&#x20; animation-delay: .15s;

}





@keyframes statEnter {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(12px);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0);

&#x20; }



}





.stat-card:hover {



&#x20; transform: translateY(-3px);



&#x20; border-color: #c9dce9;



&#x20; box-shadow:

&#x20;   0 10px 25px rgba(36,59,83,.10);

}





.stat-icon {



&#x20; width: 40px;

&#x20; height: 40px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; flex-shrink: 0;



&#x20; border-radius: 10px;



&#x20; background: var(--blue-soft);



&#x20; color: var(--blue);



&#x20; font-size: 20px;

}





.stat-info {



&#x20; display: flex;



&#x20; flex-direction: column;



&#x20; gap: 3px;

}





.stat-val {



&#x20; color: var(--navy);



&#x20; font-size: 21px;



&#x20; font-weight: 700;



&#x20; line-height: 1;

}





.stat-name {



&#x20; color: var(--text-light);



&#x20; font-size: 11px;



&#x20; font-weight: 500;

}





/\* =========================================================

&#x20;  FILTER TABS

&#x20;  ========================================================= \*/



.filter-tabs {



&#x20; max-width: 1180px;



&#x20; margin: 25px auto 0;



&#x20; padding: 0 24px;



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 5px;



&#x20; border-bottom: 1px solid var(--border);



&#x20; flex-wrap: wrap;

}





.filter-tab {



&#x20; position: relative;



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 6px;



&#x20; padding: 12px 15px;



&#x20; border: none;



&#x20; background: transparent;



&#x20; color: var(--text-light);



&#x20; font-size: 12px;



&#x20; font-weight: 600;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   color .2s ease;

}





.filter-tab::after {



&#x20; content: "";



&#x20; position: absolute;



&#x20; left: 12px;

&#x20; right: 12px;

&#x20; bottom: -1px;



&#x20; height: 2px;



&#x20; background: var(--blue);



&#x20; transform: scaleX(0);



&#x20; transition:

&#x20;   transform .25s ease;

}





.filter-tab:hover {



&#x20; color: var(--blue);

}





.filter-tab.active {



&#x20; color: var(--blue);

}





.filter-tab.active::after {



&#x20; transform: scaleX(1);

}





.tab-count {



&#x20; min-width: 17px;



&#x20; height: 17px;



&#x20; padding: 0 5px;



&#x20; display: inline-flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 20px;



&#x20; background: #edf2f7;



&#x20; color: var(--text-light);



&#x20; font-size: 9px;

}





.filter-tab.active .tab-count {



&#x20; background: var(--blue-soft);



&#x20; color: var(--blue);

}





/\* =========================================================

&#x20;  LIST CONTROLS

&#x20;  ========================================================= \*/



.list-controls {



&#x20; max-width: 1180px;



&#x20; margin: 18px auto 0;



&#x20; padding: 0 24px;



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: space-between;



&#x20; gap: 12px;

}





.search-mini-wrap {



&#x20; position: relative;



&#x20; width: 300px;

}





.search-mini-wrap .fa {



&#x20; position: absolute;



&#x20; left: 13px;

&#x20; top: 50%;



&#x20; transform: translateY(-50%);



&#x20; color: #9fb0c0;



&#x20; font-size: 12px;



&#x20; transition:

&#x20;   color .2s ease;

}





.search-mini {



&#x20; width: 100%;



&#x20; height: 38px;



&#x20; box-sizing: border-box;



&#x20; padding: 0 13px 0 35px;



&#x20; border: 1px solid var(--border);



&#x20; border-radius: 8px;



&#x20; outline: none;



&#x20; background: #ffffff;



&#x20; color: var(--text);



&#x20; font-size: 12px;



&#x20; transition:

&#x20;   border-color .25s ease,

&#x20;   box-shadow .25s ease;

}





.search-mini::placeholder {



&#x20; color: #9fb0c0;

}





.search-mini:focus {



&#x20; border-color: #79b5d5;



&#x20; box-shadow:

&#x20;   0 0 0 3px rgba(23,105,170,.08);

}





.search-mini:focus + \* {



&#x20; color: var(--blue);

}





.sort-mini {



&#x20; height: 38px;



&#x20; padding: 0 12px;



&#x20; border: 1px solid var(--border);



&#x20; border-radius: 8px;



&#x20; background: #ffffff;



&#x20; color: var(--text-light);



&#x20; font-size: 11px;



&#x20; outline: none;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   border-color .2s ease,

&#x20;   box-shadow .2s ease;

}





.sort-mini:focus {



&#x20; border-color: #79b5d5;



&#x20; box-shadow:

&#x20;   0 0 0 3px rgba(23,105,170,.07);

}





/\* =========================================================

&#x20;  LOADING

&#x20;  ========================================================= \*/



.loading-center {



&#x20; text-align: center;



&#x20; padding: 70px 20px;



&#x20; color: var(--text-light);



&#x20; animation: fadeIn .3s ease;

}





.loading-center p {



&#x20; margin: 12px 0 0;



&#x20; font-size: 12px;

}





.spinner-ring {



&#x20; display: inline-block;



&#x20; width: 34px;

&#x20; height: 34px;



&#x20; border: 3px solid #dce6ee;



&#x20; border-top-color: var(--blue);



&#x20; border-radius: 50%;



&#x20; animation: spin .75s linear infinite;

}





@keyframes spin {



&#x20; to {

&#x20;   transform: rotate(360deg);

&#x20; }



}





@keyframes fadeIn {



&#x20; from {

&#x20;   opacity: 0;

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20; }



}





/\* =========================================================

&#x20;  EMPTY STATE

&#x20;  ========================================================= \*/



.empty-appts {



&#x20; max-width: 700px;



&#x20; margin: 40px auto;



&#x20; padding: 55px 25px;



&#x20; text-align: center;



&#x20; background: #ffffff;



&#x20; border: 1px solid var(--border-light);



&#x20; border-radius: 15px;



&#x20; animation: fadeUp .4s ease both;

}





.empty-emoji {



&#x20; width: 58px;

&#x20; height: 58px;



&#x20; margin: 0 auto 17px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 50%;



&#x20; background: #edf4f9;



&#x20; font-size: 25px;

}





.empty-appts h3 {



&#x20; margin: 0 0 7px;



&#x20; color: var(--text);



&#x20; font-size: 18px;

}





.empty-appts p {



&#x20; margin: 0 0 20px;



&#x20; color: var(--text-light);



&#x20; font-size: 12px;

}





.btn-book-first {



&#x20; padding: 10px 18px;



&#x20; border: none;



&#x20; border-radius: 8px;



&#x20; background: var(--blue);



&#x20; color: #ffffff;



&#x20; font-size: 12px;



&#x20; font-weight: 700;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   background .2s ease,

&#x20;   transform .2s ease;

}





.btn-book-first:hover {



&#x20; background: #125b92;



&#x20; transform: translateY(-1px);

}





@keyframes fadeUp {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(12px);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0);

&#x20; }



}





/\* =========================================================

&#x20;  APPOINTMENT LIST

&#x20;  ========================================================= \*/



.appts-list {



&#x20; max-width: 1180px;



&#x20; margin: 5px auto 0;



&#x20; padding: 0 24px;



&#x20; display: flex;



&#x20; flex-direction: column;



&#x20; gap: 12px;

}





/\* =========================================================

&#x20;  APPOINTMENT CARD

&#x20;  ========================================================= \*/



.appt-card {



&#x20; position: relative;



&#x20; display: flex;



&#x20; overflow: hidden;



&#x20; background: #ffffff;



&#x20; border: 1px solid var(--border-light);



&#x20; border-radius: 13px;



&#x20; box-shadow:

&#x20;   0 2px 7px rgba(36,59,83,.035);



&#x20; animation: cardEnter .45s ease both;



&#x20; transition:

&#x20;   transform .28s ease,

&#x20;   box-shadow .28s ease,

&#x20;   border-color .28s ease;

}





.appt-card:nth-child(2) {

&#x20; animation-delay: .04s;

}



.appt-card:nth-child(3) {

&#x20; animation-delay: .08s;

}



.appt-card:nth-child(4) {

&#x20; animation-delay: .12s;

}





.appt-card:hover {



&#x20; transform: translateY(-3px);



&#x20; border-color: #cedde8;



&#x20; box-shadow:

&#x20;   0 10px 28px rgba(36,59,83,.08);

}





@keyframes cardEnter {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(15px);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0);

&#x20; }



}





/\* accent \*/



.appt-accent-bar {



&#x20; width: 4px;



&#x20; flex-shrink: 0;



&#x20; opacity: .9;

}





/\* =========================================================

&#x20;  CONTENT

&#x20;  ========================================================= \*/



.appt-content {



&#x20; flex: 1;



&#x20; min-width: 0;



&#x20; padding: 18px 21px 16px;

}





/\* =========================================================

&#x20;  TOP

&#x20;  ========================================================= \*/



.appt-top {



&#x20; display: flex;



&#x20; align-items: flex-start;



&#x20; justify-content: space-between;



&#x20; gap: 15px;



&#x20; margin-bottom: 14px;

}





.appt-title-group {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 12px;



&#x20; min-width: 0;

}





.appt-icon {



&#x20; width: 43px;

&#x20; height: 43px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; flex-shrink: 0;



&#x20; border-radius: 10px;



&#x20; background: #edf6fb;



&#x20; font-size: 20px;



&#x20; transition:

&#x20;   transform .25s ease;

}





.appt-card:hover .appt-icon {



&#x20; transform: scale(1.06);

}





.appt-test-name {



&#x20; margin: 0 0 4px;



&#x20; color: var(--text);



&#x20; font-size: 15px;



&#x20; font-weight: 700;



&#x20; line-height: 1.3;

}





.appt-number {



&#x20; color: #91a4b6;



&#x20; font-family:

&#x20;   "Courier New",

&#x20;   monospace;



&#x20; font-size: 10px;

}





.appt-status-wrap {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: flex-end;



&#x20; flex-wrap: wrap;



&#x20; gap: 6px;

}





/\* =========================================================

&#x20;  STATUS

&#x20;  ========================================================= \*/



.status-pill {



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 5px;



&#x20; padding: 5px 10px;



&#x20; border-radius: 20px;



&#x20; font-size: 10px;



&#x20; font-weight: 700;



&#x20; white-space: nowrap;

}





.approval-pill {



&#x20; padding: 5px 9px;



&#x20; border-radius: 20px;



&#x20; font-size: 9px;



&#x20; font-weight: 700;



&#x20; white-space: nowrap;

}





.approval-requested {



&#x20; background: var(--amber-bg);



&#x20; color: var(--amber);

}





.approval-approved {



&#x20; background: var(--green-bg);



&#x20; color: var(--green);

}





.approval-rejected {



&#x20; background: var(--red-bg);



&#x20; color: var(--red);

}





/\* =========================================================

&#x20;  META

&#x20;  ========================================================= \*/



.appt-meta {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; flex-wrap: wrap;



&#x20; gap: 8px;



&#x20; padding-bottom: 13px;



&#x20; border-bottom: 1px solid #edf1f5;

}





.meta-chip {



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 6px;



&#x20; padding: 5px 9px;



&#x20; border-radius: 6px;



&#x20; background: #f7f9fb;



&#x20; color: var(--text-light);



&#x20; font-size: 10px;



&#x20; transition:

&#x20;   background .2s ease;

}





.appt-card:hover .meta-chip {



&#x20; background: #f3f7fa;

}





.meta-chip .fa {



&#x20; color: #6b9dbb;



&#x20; font-size: 10px;

}





/\* =========================================================

&#x20;  INFORMATION

&#x20;  ========================================================= \*/



.appt-info-row {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; flex-wrap: wrap;



&#x20; gap: 7px;



&#x20; margin-top: 11px;

}





.info-badge {



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 5px;



&#x20; padding: 5px 8px;



&#x20; border-radius: 6px;



&#x20; font-size: 10px;

}





.info-badge strong {



&#x20; font-weight: 700;

}





.pay-paid {



&#x20; background: var(--green-bg);



&#x20; color: var(--green);

}





.pay-pending {



&#x20; background: var(--amber-bg);



&#x20; color: var(--amber);

}





.pay-unpaid {



&#x20; background: var(--red-bg);



&#x20; color: var(--red);

}





.approval-info {



&#x20; background: #edf4fb;



&#x20; color: #356a91;

}





.conf-badge {



&#x20; background: #f0f8f5;



&#x20; color: #368267;

}





/\* =========================================================

&#x20;  NOTES

&#x20;  ========================================================= \*/



.appt-notes {



&#x20; margin-top: 10px;



&#x20; padding: 8px 11px;



&#x20; border-left: 2px solid #cbd9e5;



&#x20; border-radius: 0 6px 6px 0;



&#x20; background: #f8fafc;



&#x20; color: var(--text-light);



&#x20; font-size: 10px;



&#x20; line-height: 1.5;

}





.appt-notes .fa {



&#x20; margin-right: 5px;



&#x20; color: #829ab1;

}





/\* =========================================================

&#x20;  REJECTION

&#x20;  ========================================================= \*/



.rejection-banner {



&#x20; display: flex;



&#x20; align-items: flex-start;



&#x20; gap: 9px;



&#x20; margin-top: 10px;



&#x20; padding: 9px 11px;



&#x20; border: 1px solid #f2d2d2;



&#x20; border-radius: 7px;



&#x20; background: #fff7f7;



&#x20; color: var(--red);



&#x20; font-size: 10px;



&#x20; line-height: 1.5;

}





.rejection-banner i {



&#x20; margin-top: 1px;

}





/\* =========================================================

&#x20;  ACTIONS

&#x20;  ========================================================= \*/



.appt-actions {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; flex-wrap: wrap;



&#x20; gap: 7px;



&#x20; margin-top: 14px;

}





.appt-action-btn {



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 6px;



&#x20; padding: 7px 12px;



&#x20; border: 1px solid transparent;



&#x20; border-radius: 7px;



&#x20; font-size: 10px;



&#x20; font-weight: 700;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   transform .2s ease,

&#x20;   background .2s ease,

&#x20;   border-color .2s ease;

}





.appt-action-btn:hover {



&#x20; transform: translateY(-1px);

}





.btn-view {



&#x20; background: #edf5fc;



&#x20; color: #28658f;

}





.btn-view:hover {



&#x20; background: #e2f0fa;



&#x20; border-color: #d2e6f3;

}





.btn-cancel {



&#x20; background: #fff1f1;



&#x20; color: #bd4848;

}





.btn-cancel:hover {



&#x20; background: #ffe7e7;

}





.btn-report {



&#x20; background: #edf8f3;



&#x20; color: #27805f;

}





.btn-report:hover {



&#x20; background: #e3f4ec;

}





.date-chip {



&#x20; margin-left: auto;



&#x20; color: #9aabba;



&#x20; font-size: 9px;



&#x20; white-space: nowrap;

}





/\* =========================================================

&#x20;  MODAL

&#x20;  ========================================================= \*/



.modal-overlay {



&#x20; position: fixed;



&#x20; inset: 0;



&#x20; z-index: 9999;



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: center;



&#x20; padding: 20px;



&#x20; background: rgba(16,42,67,.48);



&#x20; backdrop-filter: blur(3px);



&#x20; animation: overlayIn .2s ease both;

}





@keyframes overlayIn {



&#x20; from {

&#x20;   opacity: 0;

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20; }



}





.modal-box {



&#x20; width: 100%;



&#x20; max-width: 570px;



&#x20; max-height: 90vh;



&#x20; overflow: auto;



&#x20; background: #ffffff;



&#x20; border-radius: 14px;



&#x20; box-shadow:

&#x20;   0 24px 70px rgba(16,42,67,.24);



&#x20; animation: modalIn .28s cubic-bezier(.2,.8,.2,1) both;

}





@keyframes modalIn {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(15px) scale(.98);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0) scale(1);

&#x20; }



}





/\* =========================================================

&#x20;  MODAL HEADER

&#x20;  ========================================================= \*/



.modal-header {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: space-between;



&#x20; padding: 17px 21px;



&#x20; background: var(--navy);



&#x20; color: #ffffff;

}





.modal-header h3 {



&#x20; margin: 0;



&#x20; font-size: 16px;



&#x20; font-weight: 700;

}





.modal-close {



&#x20; width: 30px;

&#x20; height: 30px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border: none;



&#x20; border-radius: 7px;



&#x20; background: rgba(255,255,255,.08);



&#x20; color: #ffffff;



&#x20; font-size: 15px;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   background .2s ease,

&#x20;   transform .2s ease;

}





.modal-close:hover {



&#x20; background: rgba(255,255,255,.16);



&#x20; transform: rotate(5deg);

}





/\* =========================================================

&#x20;  MODAL BODY

&#x20;  ========================================================= \*/



.modal-body {



&#x20; padding: 22px;

}





.detail-grid {



&#x20; display: grid;



&#x20; grid-template-columns: 1fr 1fr;



&#x20; gap: 0;



&#x20; border: 1px solid var(--border-light);



&#x20; border-radius: 9px;



&#x20; overflow: hidden;

}





.detail-item {



&#x20; display: flex;



&#x20; flex-direction: column;



&#x20; gap: 4px;



&#x20; min-height: 58px;



&#x20; padding: 12px 14px;



&#x20; border-right: 1px solid var(--border-light);



&#x20; border-bottom: 1px solid var(--border-light);



&#x20; background: #ffffff;

}





.detail-item:nth-child(even) {



&#x20; border-right: none;

}





.detail-item.full {



&#x20; grid-column: 1 / -1;



&#x20; border-right: none;

}





.detail-key {



&#x20; color: #8ca0b3;



&#x20; font-size: 9px;



&#x20; font-weight: 700;



&#x20; letter-spacing: .6px;



&#x20; text-transform: uppercase;

}





.detail-val {



&#x20; color: var(--text);



&#x20; font-size: 12px;



&#x20; font-weight: 600;



&#x20; line-height: 1.4;

}





.detail-val.mono {



&#x20; color: var(--blue);



&#x20; font-family:

&#x20;   "Courier New",

&#x20;   monospace;



&#x20; font-size: 10px;

}





.detail-val.paid-green {



&#x20; color: var(--green);



&#x20; font-size: 14px;

}





/\* =========================================================

&#x20;  MODAL FOOTER

&#x20;  ========================================================= \*/



.modal-footer {



&#x20; display: flex;



&#x20; justify-content: flex-end;



&#x20; padding: 14px 21px;



&#x20; border-top: 1px solid var(--border-light);



&#x20; background: #fbfcfd;

}





.btn-close-modal {



&#x20; padding: 8px 18px;



&#x20; border: none;



&#x20; border-radius: 7px;



&#x20; background: var(--navy);



&#x20; color: #ffffff;



&#x20; font-size: 11px;



&#x20; font-weight: 700;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   background .2s ease,

&#x20;   transform .2s ease;

}





.btn-close-modal:hover {



&#x20; background: #183f61;



&#x20; transform: translateY(-1px);

}





/\* =========================================================

&#x20;  RESPONSIVE

&#x20;  ========================================================= \*/



@media (max-width: 800px) {



&#x20; .appts-header {



&#x20;   padding: 32px 24px 52px;



&#x20;   align-items: flex-start;



&#x20;   flex-direction: column;

&#x20; }





&#x20; .header-title {



&#x20;   font-size: 27px;

&#x20; }





&#x20; .stats-bar {



&#x20;   grid-template-columns:

&#x20;     repeat(2, 1fr);



&#x20;   padding-left: 16px;

&#x20;   padding-right: 16px;

&#x20; }





&#x20; .filter-tabs,

&#x20; .list-controls,

&#x20; .appts-list {



&#x20;   padding-left: 16px;

&#x20;   padding-right: 16px;

&#x20; }





&#x20; .list-controls {



&#x20;   align-items: stretch;



&#x20;   flex-direction: column;

&#x20; }





&#x20; .search-mini-wrap {



&#x20;   width: 100%;



&#x20;   max-width: none;

&#x20; }





&#x20; .sort-mini {



&#x20;   width: 100%;

&#x20; }





&#x20; .appt-top {



&#x20;   align-items: flex-start;



&#x20;   flex-direction: column;

&#x20; }





&#x20; .appt-status-wrap {



&#x20;   justify-content: flex-start;

&#x20; }





&#x20; .date-chip {



&#x20;   margin-left: 0;

&#x20; }



}





@media (max-width: 520px) {



&#x20; .appts-header {



&#x20;   padding: 28px 18px 48px;



&#x20;   border-radius: 0 0 25px 25px;

&#x20; }





&#x20; .header-title {



&#x20;   font-size: 24px;

&#x20; }





&#x20; .header-sub {



&#x20;   font-size: 12px;

&#x20; }





&#x20; .btn-book-new {



&#x20;   width: 100%;



&#x20;   justify-content: center;

&#x20; }





&#x20; .stats-bar {



&#x20;   grid-template-columns: 1fr;



&#x20; }





&#x20; .filter-tabs {



&#x20;   overflow-x: auto;



&#x20;   flex-wrap: nowrap;



&#x20;   scrollbar-width: none;

&#x20; }





&#x20; .filter-tabs::-webkit-scrollbar {



&#x20;   display: none;

&#x20; }





&#x20; .filter-tab {



&#x20;   flex-shrink: 0;

&#x20; }





&#x20; .appt-content {



&#x20;   padding: 15px;

&#x20; }





&#x20; .appt-meta {



&#x20;   gap: 5px;

&#x20; }





&#x20; .meta-chip {



&#x20;   font-size: 9px;

&#x20; }





&#x20; .detail-grid {



&#x20;   grid-template-columns: 1fr;

&#x20; }





&#x20; .detail-item,

&#x20; .detail-item:nth-child(even) {



&#x20;   border-right: none;

&#x20; }





&#x20; .detail-item.full {



&#x20;   grid-column: auto;

&#x20; }



}

#### **Client controller:**

api.controller=function() {

&#x20; var c = this;



&#x20; // ── PAGE IDs (confirmed from your ServiceNow Pages list) ──

&#x20; var PAGE\_IDS = {

&#x20;   home:       'test\_catalog',   // ← CORRECT page ID from your screenshot

&#x20;   labReports: 'lab\_reports'

&#x20; };



&#x20; c.loading = true;

&#x20; c.activeTab = 'all';

&#x20; c.searchQuery = '';

&#x20; c.sortBy = 'date\_desc';

&#x20; c.filteredAppointments = \[];

&#x20; c.showModal = false;

&#x20; c.selectedAppt = null;



&#x20; c.tabs = \[

&#x20;   { key: 'all',       label: 'All',       count: 0 },

&#x20;   { key: 'pending',   label: 'Pending',   count: 0 },

&#x20;   { key: 'confirmed', label: 'Confirmed', count: 0 },

&#x20;   { key: 'completed', label: 'Completed', count: 0 },

&#x20;   { key: 'cancelled', label: 'Cancelled', count: 0 }

&#x20; ];



&#x20; c.stats = \[

&#x20;   { icon: '📋', label: 'Total',     count: 0 },

&#x20;   { icon: '✅', label: 'Confirmed', count: 0 },

&#x20;   { icon: '⏳', label: 'Pending',   count: 0 },

&#x20;   { icon: '✔️', label: 'Completed', count: 0 }

&#x20; ];



&#x20; // ── NAVIGATION ────────────────────────────────────────────

&#x20; var \_nav = function(pageId) {

&#x20;   var portalId = window.location.pathname.split('/')\[1] || 'sp';

&#x20;   window.location.href = '/' + portalId + '?id=' + pageId;

&#x20; };



&#x20; // ── INIT ──────────────────────────────────────────────────

&#x20; // KEY FIX: ServiceNow populates c.data synchronously BEFORE this runs.

&#x20; // $watch('data') never fires. Just read data directly in $onInit.

&#x20; c.$onInit = function() {

&#x20;   c.loading = false;

&#x20;   c.buildStats();

&#x20;   c.filterAppointments();

&#x20; };



&#x20; c.buildStats = function() {

&#x20;   var appts = c.data.appointments || \[];

&#x20;   c.stats\[0].count = appts.length;

&#x20;   c.stats\[1].count = appts.filter(function(a) { return a.status === 'confirmed'; }).length;

&#x20;   c.stats\[2].count = appts.filter(function(a) { return a.status === 'pending';   }).length;

&#x20;   c.stats\[3].count = appts.filter(function(a) { return a.status === 'completed'; }).length;

&#x20;   c.tabs.forEach(function(tab) {

&#x20;     tab.count = (tab.key === 'all')

&#x20;       ? appts.length

&#x20;       : appts.filter(function(a) { return a.status === tab.key; }).length;

&#x20;   });

&#x20; };



&#x20; c.setTab = function(key) { c.activeTab = key; c.filterAppointments(); };



&#x20; c.filterAppointments = function() {

&#x20;   var appts = angular.copy(c.data.appointments || \[]);

&#x20;   var q   = (c.searchQuery || '').toLowerCase();

&#x20;   var tab = c.activeTab;

&#x20;   c.filteredAppointments = appts.filter(function(a) {

&#x20;     var matchTab    = (tab === 'all') || (a.status === tab);

&#x20;     var matchSearch = !q ||

&#x20;       (a.test\_name          \&\& a.test\_name.toLowerCase().indexOf(q) !== -1) ||

&#x20;       (a.appointment\_number \&\& a.appointment\_number.toLowerCase().indexOf(q) !== -1) ||

&#x20;       (a.test\_category      \&\& a.test\_category.toLowerCase().indexOf(q) !== -1);

&#x20;     return matchTab \&\& matchSearch;

&#x20;   });

&#x20;   c.sortAppointments();

&#x20; };



&#x20; c.sortAppointments = function() {

&#x20;   c.filteredAppointments.sort(function(a, b) {

&#x20;     if (c.sortBy === 'date\_asc')  return (a.scheduled\_date || '').localeCompare(b.scheduled\_date || '');

&#x20;     if (c.sortBy === 'date\_desc') return (b.scheduled\_date || '').localeCompare(a.scheduled\_date || '');

&#x20;     if (c.sortBy === 'status')    return (a.status || '').localeCompare(b.status || '');

&#x20;     return 0;

&#x20;   });

&#x20; };



&#x20; // ── STATUS HELPERS ────────────────────────────────────────

&#x20; var STATUS\_MAP = {

&#x20;   'pending':   { color:'#f59e0b', bg:'#fef3c7', icon:'⏳', label:'Pending'   },

&#x20;   'confirmed': { color:'#3b82f6', bg:'#dbeafe', icon:'✅', label:'Confirmed' },

&#x20;   'completed': { color:'#10b981', bg:'#dcfce7', icon:'✔️', label:'Completed' },

&#x20;   'cancelled': { color:'#6b7280', bg:'#f1f5f9', icon:'🚫', label:'Cancelled' },

&#x20;   'rejected':  { color:'#ef4444', bg:'#fee2e2', icon:'❌', label:'Rejected'  }

&#x20; };

&#x20; var \_statusProp = function(s, prop, fallback) {

&#x20;   return (STATUS\_MAP\[s] \&\& STATUS\_MAP\[s]\[prop]) ? STATUS\_MAP\[s]\[prop] : fallback;

&#x20; };

&#x20; c.getStatusColor = function(s) { return \_statusProp(s, 'color', '#94a3b8'); };

&#x20; c.getStatusBg    = function(s) { return \_statusProp(s, 'bg',    '#f1f5f9'); };

&#x20; c.getStatusIcon  = function(s) { return \_statusProp(s, 'icon',  '•');       };

&#x20; c.getStatusLabel = function(s) { return \_statusProp(s, 'label', s);         };



&#x20; c.getApprovalLabel = function(s) {

&#x20;   var m = { 'requested':'Approval Requested','approved':'✅ Approved','rejected':'❌ Rejected' };

&#x20;   return m\[s] || s;

&#x20; };

&#x20; c.getPaymentLabel = function(s) {

&#x20;   var m = { 'paid':'✓ Paid','pending':'Payment Pending','unpaid':'Unpaid','refunded':'Refunded' };

&#x20;   return m\[s] || (s || 'N/A');

&#x20; };

&#x20; c.getCategoryIcon = function(cat) {

&#x20;   var icons = { 'blood':'🩸','urine':'🧪','imaging':'🩻','cardiology':'❤️',

&#x20;                 'neurology':'🧠','genetics':'🧬','pathology':'🔬' };

&#x20;   if (!cat) return '🔬';

&#x20;   var k = cat.toLowerCase();

&#x20;   for (var key in icons) { if (k.indexOf(key) !== -1) return icons\[key]; }

&#x20;   return '🔬';

&#x20; };



&#x20; c.canCancel = function(appt) {

&#x20;   return appt.status === 'pending' || appt.status === 'confirmed';

&#x20; };



&#x20; // CANCEL 

&#x20; c.cancelAppointment = function(appt) {

&#x20;   if (!confirm('Are you sure you want to cancel appointment ' + appt.appointment\_number + '?')) return;

&#x20;   c.server.get({ action: 'cancel\_appointment', appointment\_sys\_id: appt.sys\_id })

&#x20;     .then(function(response) {

&#x20;       if (response.data.success) {

&#x20;         appt.status = 'cancelled';

&#x20;         c.buildStats();

&#x20;         c.filterAppointments();

&#x20;         alert('Appointment cancelled successfully.');

&#x20;       } else {

&#x20;         alert('Error: ' + (response.data.error || 'Failed to cancel.'));

&#x20;       }

&#x20;     });

&#x20; };



&#x20; // ── MODAL ─────────────────────────────────────────────────

&#x20; c.viewDetails = function(appt) { c.selectedAppt = appt; c.showModal = true;  };

&#x20; c.closeModal  = function()     { c.showModal = false;   c.selectedAppt = null; };



&#x20; // ── NAVIGATION ────────────────────────────────────────────

&#x20; // KEY FIX: "Book New Test" now goes to correct page ID "test\_catalog"

&#x20; c.bookNew   = function() { \_nav(PAGE\_IDS.home); };

&#x20; c.viewReport = function(appt) { \_nav(PAGE\_IDS.labReports); };

}



#### **Server script**



(function() {

&#x20; data.appointments = \[];



&#x20; try {

&#x20;   var currentUser  = gs.getUser();

&#x20;   var userID       = gs.getUserID();

&#x20;   var userEmail    = currentUser.getEmail() || '';

&#x20;   var userName     = gs.getUserName() || '';



&#x20;   // ── APPROACH 1: Find patient records linked to this sys\_user ──────

&#x20;   var patientSysIds = \[];

&#x20;   var patientMap    = {};  // sys\_id → true (dedup)



&#x20;   // By user reference field

&#x20;   var patGr = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;   patGr.addQuery('user', userID);

&#x20;   patGr.query();

&#x20;   while (patGr.next()) {

&#x20;     var pid = patGr.getUniqueValue();

&#x20;     if (!patientMap\[pid]) { patientMap\[pid] = true; patientSysIds.push(pid); }

&#x20;   }



&#x20;   // By email (catches cases where email in form ≠ ServiceNow user email)

&#x20;   if (userEmail) {

&#x20;     var patEmailGr = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;     patEmailGr.addQuery('email', userEmail);

&#x20;     patEmailGr.query();

&#x20;     while (patEmailGr.next()) {

&#x20;       var eid = patEmailGr.getUniqueValue();

&#x20;       if (!patientMap\[eid]) { patientMap\[eid] = true; patientSysIds.push(eid); }

&#x20;     }

&#x20;   }



&#x20;   // ── APPROACH 2: Find appointments created\_by this user ────────────

&#x20;   // KEY FIX: catches bookings where patient email ≠ logged-in user email

&#x20;   var apptSysIds   = \[];

&#x20;   var apptMap      = {};  // dedup

&#x20;   var apptDataMap  = {};  // sys\_id → raw appointment GlideRecord data



&#x20;   var createdByGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;   createdByGr.addQuery('created\_by', userID);

&#x20;   createdByGr.orderByDesc('sys\_created\_on');

&#x20;   createdByGr.query();

&#x20;   while (createdByGr.next()) {

&#x20;     var aid = createdByGr.getUniqueValue();

&#x20;     if (!apptMap\[aid]) {

&#x20;       apptMap\[aid] = true;

&#x20;       apptSysIds.push(aid);



&#x20;       // Also collect patient IDs from these appointments

&#x20;       var pRef = createdByGr.getValue('patient');

&#x20;       if (pRef \&\& !patientMap\[pRef]) {

&#x20;         patientMap\[pRef] = true;

&#x20;         patientSysIds.push(pRef);

&#x20;       }

&#x20;     }

&#x20;   }



&#x20;   // ── APPROACH 3: Appointments linked to any patient record found ────

&#x20;   if (patientSysIds.length > 0) {

&#x20;     var apptPatGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;     apptPatGr.addQuery('patient', 'IN', patientSysIds.join(','));

&#x20;     apptPatGr.orderByDesc('sys\_created\_on');

&#x20;     apptPatGr.query();

&#x20;     while (apptPatGr.next()) {

&#x20;       var apid = apptPatGr.getUniqueValue();

&#x20;       if (!apptMap\[apid]) {

&#x20;         apptMap\[apid] = true;

&#x20;         apptSysIds.push(apid);

&#x20;       }

&#x20;     }

&#x20;   }



&#x20;   if (apptSysIds.length === 0) {

&#x20;     data.appointments = \[];

&#x20;     return;

&#x20;   }



&#x20;   // ── FETCH FULL APPOINTMENT DATA ────────────────────────────────────

&#x20;   var finalGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;   finalGr.addQuery('sys\_id', 'IN', apptSysIds.join(','));

&#x20;   finalGr.orderByDesc('sys\_created\_on');

&#x20;   finalGr.query();



&#x20;   while (finalGr.next()) {



&#x20;     // Get test details

&#x20;     var testName     = '';

&#x20;     var testCategory = '';

&#x20;     var testRef      = finalGr.getValue('test');

&#x20;     if (testRef) {

&#x20;       var testGr = new GlideRecord('x\_1989050\_medica\_0\_diagnostic\_test');

&#x20;       if (testGr.get(testRef)) {

&#x20;         testName     = testGr.getValue('test\_name') || '';

&#x20;         testCategory = testGr.getDisplayValue('category') || testGr.getValue('category') || '';

&#x20;       }

&#x20;     }



&#x20;     // Check if report exists

&#x20;     var hasReport = false;

&#x20;     var reportGr  = new GlideRecord('x\_1989050\_medica\_0\_report\_table');

&#x20;     reportGr.addQuery('appointment', finalGr.getUniqueValue());

&#x20;     reportGr.setLimit(1);

&#x20;     reportGr.query();

&#x20;     if (reportGr.next()) { hasReport = true; }



&#x20;     // Approved by name

&#x20;     var approvedByName = '';

&#x20;     var approvedByRef  = finalGr.getValue('approved\_by');

&#x20;     if (approvedByRef) {

&#x20;       var approverGr = new GlideRecord('sys\_user');

&#x20;       if (approverGr.get(approvedByRef)) {

&#x20;         approvedByName = approverGr.getDisplayValue('name') || '';

&#x20;       }

&#x20;     }



&#x20;     // Format dates safely

&#x20;     var scheduledRaw = finalGr.getValue('scheduled\_date') || '';

&#x20;     var scheduledDisplay = '';

&#x20;     if (scheduledRaw) {

&#x20;       try {

&#x20;         var gdt = new GlideDateTime(scheduledRaw);

&#x20;         scheduledDisplay = gdt.getLocalDate().getLocalDate();

&#x20;       } catch(dateErr) {

&#x20;         scheduledDisplay = scheduledRaw.split(' ')\[0] || scheduledRaw;

&#x20;       }

&#x20;     }



&#x20;     var createdOn = finalGr.getDisplayValue('sys\_created\_on') || '';



&#x20;     data.appointments.push({

&#x20;       sys\_id:              finalGr.getUniqueValue(),

&#x20;       appointment\_number:  finalGr.getValue('appointment\_number') || '',

&#x20;       status:              finalGr.getValue('status') || 'pending',

&#x20;       approval\_status:     finalGr.getValue('approval\_status') || '',

&#x20;       payment\_status:      finalGr.getValue('payment\_status') || '',

&#x20;       scheduled\_date:      scheduledRaw,

&#x20;       scheduled\_date\_display: scheduledDisplay,

&#x20;       slot\_time:           finalGr.getValue('slot\_time') || '',

&#x20;       total\_amount:        parseFloat(finalGr.getValue('total\_amount')) || 0,

&#x20;       notes:               finalGr.getValue('notes') || '',

&#x20;       rejection\_reason:    finalGr.getValue('rejection\_reason') || '',

&#x20;       confirmation\_sent:   finalGr.getValue('confirmation\_sent') === '1' || finalGr.getValue('confirmation\_sent') === true,

&#x20;       test\_name:           testName,

&#x20;       test\_category:       testCategory,

&#x20;       approved\_by\_name:    approvedByName,

&#x20;       has\_report:          hasReport,

&#x20;       created\_on\_display:  createdOn

&#x20;     });

&#x20;   }



&#x20;   // ── HANDLE CANCEL ACTION ───────────────────────────────────────────

&#x20;   if (input \&\& input.action === 'cancel\_appointment') {

&#x20;     var cancelGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;     if (cancelGr.get(input.appointment\_sys\_id)) {



&#x20;       // Verify ownership: created\_by OR patient belongs to this user

&#x20;       var isOwner = false;

&#x20;       if (cancelGr.getValue('created\_by') === userID) {

&#x20;         isOwner = true;

&#x20;       } else {

&#x20;         var cancelPatId = cancelGr.getValue('patient');

&#x20;         if (cancelPatId \&\& patientSysIds.indexOf(cancelPatId) !== -1) {

&#x20;           isOwner = true;

&#x20;         }

&#x20;       }



&#x20;       if (isOwner) {

&#x20;         cancelGr.setValue('status', 'cancelled');

&#x20;         cancelGr.update();

&#x20;         data.success = true;



&#x20;         // Send cancellation email

&#x20;         try {

&#x20;           var patEmail2 = '';

&#x20;           var patGr2 = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;           if (patGr2.get(cancelGr.getValue('patient'))) {

&#x20;             patEmail2 = patGr2.getValue('email') || '';

&#x20;           }

&#x20;           if (patEmail2) {

&#x20;             var emailer = new GlideEmailOutbound();

&#x20;             emailer.setTo(patEmail2);

&#x20;             emailer.setSubject('Appointment Cancelled: ' + cancelGr.getValue('appointment\_number'));

&#x20;             emailer.setBody('<p>Your appointment <strong>' +

&#x20;               cancelGr.getValue('appointment\_number') +

&#x20;               '</strong> has been cancelled. If this was a mistake, please book again.</p>');

&#x20;             emailer.save();

&#x20;           }

&#x20;         } catch(emailErr) {

&#x20;           gs.warn('Cancel email error: ' + emailErr.message);

&#x20;         }



&#x20;       } else {

&#x20;         data.error = 'Unauthorized';

&#x20;       }

&#x20;     } else {

&#x20;       data.error = 'Appointment not found';

&#x20;     }

&#x20;   }



&#x20; } catch(e) {

&#x20;   gs.error('My Appointments Widget Error: ' + e.message);

&#x20;   data.error = 'Failed to load appointments: ' + e.message;

&#x20;   data.appointments = \[];

&#x20; }

})();



