#### **MEDICAL\_TEST\_CATALOG**

#### **HTML**

<div class="med-catalog">



&#x20; <!-- ==========================================

&#x20;      HERO

&#x20;      ========================================== -->

&#x20; <section class="dc-hero">



&#x20;   <div class="hero-glow glow-one"></div>

&#x20;   <div class="hero-glow glow-two"></div>



&#x20;   <div class="dc-hero-content">



&#x20;     <div class="dc-eyebrow">

&#x20;       <span class="live-dot"></span>

&#x20;       Trusted Diagnostic Care

&#x20;     </div>



&#x20;     <h1>

&#x20;       Healthcare decisions<br>

&#x20;       <span>start with clarity.</span>

&#x20;     </h1>



&#x20;     <p class="hero-description">

&#x20;       Explore reliable diagnostic tests, choose your preferred

&#x20;       appointment and access your reports — all from one place.

&#x20;     </p>



&#x20;     <!-- SEARCH -->

&#x20;     <div class="dc-search">



&#x20;       <i class="fa fa-search"></i>



&#x20;       <input

&#x20;         type="text"

&#x20;         placeholder="Search for a test or category..."

&#x20;         ng-model="c.searchQuery"

&#x20;         ng-change="c.filterTests()"

&#x20;       />



&#x20;       <button

&#x20;         ng-if="c.searchQuery"

&#x20;         ng-click="c.clearSearch()"

&#x20;         class="clear-search">

&#x20;         <i class="fa fa-times"></i>

&#x20;       </button>



&#x20;       <div class="search-action">

&#x20;         Search

&#x20;       </div>



&#x20;     </div>



&#x20;     <!-- HERO TRUST -->

&#x20;     <div class="hero-trust">



&#x20;       <span>

&#x20;         <i class="fa fa-check-circle"></i>

&#x20;         Verified Tests

&#x20;       </span>



&#x20;       <span>

&#x20;         <i class="fa fa-clock-o"></i>

&#x20;         Fast Results

&#x20;       </span>



&#x20;       <span>

&#x20;         <i class="fa fa-shield"></i>

&#x20;         Secure Records

&#x20;       </span>



&#x20;     </div>



&#x20;   </div>





&#x20;   <!-- HERO VISUAL -->

&#x20;   <div class="dc-hero-visual">



&#x20;     <div class="medical-orbit orbit-one"></div>

&#x20;     <div class="medical-orbit orbit-two"></div>



&#x20;     <div class="medical-core">

&#x20;       <div class="core-icon">

&#x20;         <i class="fa fa-heartbeat"></i>

&#x20;       </div>



&#x20;       <div class="core-pulse"></div>

&#x20;     </div>





&#x20;     <!-- FLOATING CARDS -->



&#x20;     <div class="floating-card floating-tests">



&#x20;       <div class="floating-icon">

&#x20;         <i class="fa fa-flask"></i>

&#x20;       </div>



&#x20;       <div>

&#x20;         <strong>{{c.data.totalTests}}+</strong>

&#x20;         <small>Tests Available</small>

&#x20;       </div>



&#x20;     </div>





&#x20;     <div class="floating-card floating-results">



&#x20;       <div class="floating-icon">

&#x20;         <i class="fa fa-file-text-o"></i>

&#x20;       </div>



&#x20;       <div>

&#x20;         <strong>24h</strong>

&#x20;         <small>Average Results</small>

&#x20;       </div>



&#x20;     </div>





&#x20;     <div class="floating-card floating-secure">



&#x20;       <i class="fa fa-lock"></i>



&#x20;       <span>Secure</span>



&#x20;     </div>



&#x20;   </div>



&#x20; </section>







&#x20; <!-- ==========================================

&#x20;      QUICK ACTIONS

&#x20;      ========================================== -->



&#x20; <section class="quick-section">



&#x20;   <div class="quick-card" ng-click="c.goToMyBookings()">



&#x20;     <div class="quick-icon booking">

&#x20;       <i class="fa fa-calendar-check-o"></i>

&#x20;     </div>



&#x20;     <div class="quick-text">

&#x20;       <span>Appointments</span>

&#x20;       <strong>My Bookings</strong>

&#x20;       <small>View and manage your appointments</small>

&#x20;     </div>



&#x20;     <div class="quick-arrow">

&#x20;       <i class="fa fa-arrow-right"></i>

&#x20;     </div>



&#x20;   </div>





&#x20;   <div class="quick-card" ng-click="c.goToMyReports()">



&#x20;     <div class="quick-icon reports">

&#x20;       <i class="fa fa-file-medical-o"></i>

&#x20;     </div>



&#x20;     <div class="quick-text">

&#x20;       <span>Health Records</span>

&#x20;       <strong>My Reports</strong>

&#x20;       <small>Access your diagnostic results</small>

&#x20;     </div>



&#x20;     <div class="quick-arrow">

&#x20;       <i class="fa fa-arrow-right"></i>

&#x20;     </div>



&#x20;   </div>



&#x20; </section>







&#x20; <!-- ==========================================

&#x20;      CATALOG HEADER

&#x20;      ========================================== -->



&#x20; <section class="catalog-section">



&#x20;   <div class="catalog-top">



&#x20;     <div>



&#x20;       <span class="section-kicker">

&#x20;         DIAGNOSTIC CATALOG

&#x20;       </span>



&#x20;       <h2>

&#x20;         Find the right test for you

&#x20;       </h2>



&#x20;       <p>

&#x20;         Browse our available diagnostic tests and packages.

&#x20;       </p>



&#x20;     </div>



&#x20;   </div>





&#x20;   <!-- CATEGORY FILTER -->



&#x20;   <div class="category-scroll">



&#x20;     <button

&#x20;       class="category-pill"

&#x20;       ng-class="{'selected': c.activeCategory === 'all'}"

&#x20;       ng-click="c.setCategory('all')">



&#x20;       <i class="fa fa-th"></i>

&#x20;       All Tests



&#x20;     </button>





&#x20;     <button

&#x20;       class="category-pill"

&#x20;       ng-repeat="cat in c.data.categories"

&#x20;       ng-class="{'selected': c.activeCategory === cat}"

&#x20;       ng-click="c.setCategory(cat)">



&#x20;       {{cat}}



&#x20;     </button>



&#x20;   </div>





&#x20;   <!-- RESULTS -->



&#x20;   <div class="catalog-controls">



&#x20;     <div class="result-message">



&#x20;       <span>

&#x20;         <strong>{{c.filteredTests.length}}</strong>

&#x20;         tests available

&#x20;       </span>



&#x20;       <span ng-if="c.searchQuery">

&#x20;         · Search:

&#x20;         <b>"{{c.searchQuery}}"</b>

&#x20;       </span>



&#x20;       <span ng-if="c.activeCategory !== 'all'">

&#x20;         · {{c.activeCategory}}

&#x20;       </span>



&#x20;     </div>





&#x20;     <div class="sort-control">



&#x20;       <i class="fa fa-sliders"></i>



&#x20;       <span>Sort</span>



&#x20;       <select

&#x20;         ng-model="c.sortBy"

&#x20;         ng-change="c.sortTests()">



&#x20;         <option value="name">

&#x20;           Name

&#x20;         </option>



&#x20;         <option value="price\_asc">

&#x20;           Price: Low to High

&#x20;         </option>



&#x20;         <option value="price\_desc">

&#x20;           Price: High to Low

&#x20;         </option>



&#x20;         <option value="duration">

&#x20;           Duration

&#x20;         </option>



&#x20;       </select>



&#x20;     </div>



&#x20;   </div>







&#x20;   <!-- ==========================================

&#x20;        EMPTY STATE

&#x20;        ========================================== -->



&#x20;   <div

&#x20;     class="modern-empty"

&#x20;     ng-if="c.filteredTests.length === 0">



&#x20;     <div class="empty-circle">

&#x20;       <i class="fa fa-search"></i>

&#x20;     </div>



&#x20;     <h3

&#x20;       ng-if="(c.data.tests || \[]).length === 0">



&#x20;       No diagnostic tests available



&#x20;     </h3>



&#x20;     <h3

&#x20;       ng-if="(c.data.tests || \[]).length > 0">



&#x20;       No matching tests found



&#x20;     </h3>



&#x20;     <p

&#x20;       ng-if="(c.data.tests || \[]).length === 0">



&#x20;       No active diagnostic tests are currently available.



&#x20;     </p>



&#x20;     <p

&#x20;       ng-if="(c.data.tests || \[]).length > 0">



&#x20;       Try another search term or category.



&#x20;     </p>



&#x20;     <button

&#x20;       ng-if="(c.data.tests || \[]).length > 0"

&#x20;       ng-click="c.resetFilters()">



&#x20;       <i class="fa fa-refresh"></i>

&#x20;       Reset Filters



&#x20;     </button>



&#x20;   </div>







&#x20;   <!-- ==========================================

&#x20;        TEST GRID

&#x20;        ========================================== -->



&#x20;   <div

&#x20;     class="diagnostic-grid"

&#x20;     ng-if="c.filteredTests.length > 0">





&#x20;     <article

&#x20;       class="diagnostic-card"

&#x20;       ng-repeat="test in c.filteredTests">





&#x20;       <!-- TOP -->



&#x20;       <div class="diagnostic-top">



&#x20;         <div class="test-symbol">



&#x20;           <span>

&#x20;             {{c.getCategoryIcon(test.category)}}

&#x20;           </span>



&#x20;         </div>





&#x20;         <div class="availability">



&#x20;           <span

&#x20;             class="available-dot"

&#x20;             ng-if="test.active">

&#x20;           </span>



&#x20;           <span

&#x20;             class="unavailable-dot"

&#x20;             ng-if="!test.active">

&#x20;           </span>



&#x20;           {{test.active ? 'Available' : 'Unavailable'}}



&#x20;         </div>



&#x20;       </div>





&#x20;       <!-- BODY -->



&#x20;       <div class="diagnostic-body">



&#x20;         <div class="test-category">

&#x20;           {{test.category || 'General'}}

&#x20;         </div>



&#x20;         <h3>

&#x20;           {{test.test\_name}}

&#x20;         </h3>



&#x20;         <div class="test-id">

&#x20;           TEST ID · {{test.test\_code}}

&#x20;         </div>



&#x20;         <p>

&#x20;           {{c.truncate(test.description, 110)}}

&#x20;         </p>





&#x20;         <!-- META -->



&#x20;         <div class="diagnostic-meta">



&#x20;           <div ng-if="test.test\_duration">



&#x20;             <i class="fa fa-clock-o"></i>



&#x20;             <span>

&#x20;               {{test.test\_duration}}

&#x20;             </span>



&#x20;           </div>



&#x20;           <div>



&#x20;             <i class="fa fa-flask"></i>



&#x20;             <span>

&#x20;               Lab Test

&#x20;             </span>



&#x20;           </div>



&#x20;         </div>



&#x20;       </div>





&#x20;       <!-- FOOTER -->



&#x20;       <div class="diagnostic-footer">



&#x20;         <div class="test-price">



&#x20;           <small>

&#x20;             Starting from

&#x20;           </small>



&#x20;           <strong>

&#x20;             ${{test.price | number:2}}

&#x20;           </strong>



&#x20;         </div>





&#x20;         <button

&#x20;           class="book-button"

&#x20;           ng-if="test.active"

&#x20;           ng-click="c.bookTest(test)">



&#x20;           <span>

&#x20;             Book Test

&#x20;           </span>



&#x20;           <i class="fa fa-arrow-right"></i>



&#x20;         </button>





&#x20;         <button

&#x20;           class="book-button disabled"

&#x20;           ng-if="!test.active"

&#x20;           disabled>



&#x20;           Unavailable



&#x20;         </button>



&#x20;       </div>



&#x20;     </article>



&#x20;   </div>





&#x20;   <!-- BOTTOM INFO -->



&#x20;   <div

&#x20;     class="catalog-note"

&#x20;     ng-if="c.filteredTests.length > 0">



&#x20;     <div class="note-icon">

&#x20;       <i class="fa fa-info"></i>

&#x20;     </div>



&#x20;     <div>



&#x20;       <strong>

&#x20;         Need help choosing a test?

&#x20;       </strong>



&#x20;       <span>

&#x20;         Browse categories above or search for a specific diagnostic test.

&#x20;       </span>



&#x20;     </div>



&#x20;   </div>



&#x20; </section>



</div>

#### **CSS**



/\* =========================================================

&#x20;  DIAGNOSTIC CENTER — PREMIUM UI

&#x20;  ========================================================= \*/



.med-catalog {



&#x20; --navy: #071a3d;

&#x20; --blue: #1261ff;

&#x20; --cyan: #18c8e8;

&#x20; --cyan-light: #e8fbff;



&#x20; --text: #14213d;

&#x20; --muted: #718096;

&#x20; --border: #e7edf5;

&#x20; --surface: #ffffff;

&#x20; --background: #f6f9fc;



&#x20; font-family:

&#x20;   "Inter",

&#x20;   "Segoe UI",

&#x20;   system-ui,

&#x20;   sans-serif;



&#x20; background: var(--background);

&#x20; min-height: 100vh;

&#x20; color: var(--text);



&#x20; padding-bottom: 70px;



&#x20; overflow: hidden;

}





/\* =========================================================

&#x20;  HERO

&#x20;  ========================================================= \*/



.dc-hero {



&#x20; min-height: 510px;



&#x20; padding: 70px 8%;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: space-between;



&#x20; position: relative;

&#x20; overflow: hidden;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     125deg,

&#x20;     #061638 0%,

&#x20;     #09285a 48%,

&#x20;     #073b70 100%

&#x20;   );



&#x20; border-radius: 0 0 50px 50px;

}





/\* animated background \*/



.dc-hero::before {



&#x20; content: "";



&#x20; position: absolute;



&#x20; width: 600px;

&#x20; height: 600px;



&#x20; right: -180px;

&#x20; top: -300px;



&#x20; border-radius: 50%;



&#x20; background:

&#x20;   radial-gradient(

&#x20;     circle,

&#x20;     rgba(24,200,232,.20),

&#x20;     transparent 65%

&#x20;   );



&#x20; animation: heroGlow 7s ease-in-out infinite alternate;

}





.dc-hero::after {



&#x20; content: "";



&#x20; position: absolute;



&#x20; width: 450px;

&#x20; height: 450px;



&#x20; left: -250px;

&#x20; bottom: -300px;



&#x20; border-radius: 50%;



&#x20; background:

&#x20;   radial-gradient(

&#x20;     circle,

&#x20;     rgba(18,97,255,.18),

&#x20;     transparent 65%

&#x20;   );



}





@keyframes heroGlow {



&#x20; from {

&#x20;   transform: translate(0,0) scale(1);

&#x20; }



&#x20; to {

&#x20;   transform: translate(-50px,40px) scale(1.15);

&#x20; }



}





.hero-glow {



&#x20; position: absolute;



&#x20; border-radius: 50%;



&#x20; filter: blur(2px);



&#x20; pointer-events: none;

}





.glow-one {



&#x20; width: 12px;

&#x20; height: 12px;



&#x20; background: #18c8e8;



&#x20; right: 35%;

&#x20; top: 20%;



&#x20; box-shadow:

&#x20;   0 0 30px #18c8e8;



&#x20; animation: particle 4s ease-in-out infinite;

}





.glow-two {



&#x20; width: 7px;

&#x20; height: 7px;



&#x20; background: #ffffff;



&#x20; right: 18%;

&#x20; bottom: 25%;



&#x20; opacity: .6;



&#x20; animation: particle 5s ease-in-out infinite reverse;

}





@keyframes particle {



&#x20; 0%,100% {

&#x20;   transform: translateY(0);

&#x20;   opacity: .5;

&#x20; }



&#x20; 50% {

&#x20;   transform: translateY(-25px);

&#x20;   opacity: 1;

&#x20; }



}





/\* =========================================================

&#x20;  HERO CONTENT

&#x20;  ========================================================= \*/



.dc-hero-content {



&#x20; max-width: 650px;



&#x20; position: relative;

&#x20; z-index: 5;



&#x20; animation: heroEnter .8s ease both;

}





@keyframes heroEnter {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(25px);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0);

&#x20; }



}





.dc-eyebrow {



&#x20; display: inline-flex;



&#x20; align-items: center;



&#x20; gap: 9px;



&#x20; padding: 7px 14px;



&#x20; border-radius: 30px;



&#x20; background: rgba(255,255,255,.08);



&#x20; border: 1px solid rgba(255,255,255,.12);



&#x20; color: #a8d9ff;



&#x20; font-size: 11px;



&#x20; font-weight: 700;



&#x20; letter-spacing: 1px;



&#x20; text-transform: uppercase;



&#x20; margin-bottom: 24px;

}





.live-dot {



&#x20; width: 7px;

&#x20; height: 7px;



&#x20; border-radius: 50%;



&#x20; background: #29e69a;



&#x20; box-shadow:

&#x20;   0 0 0 5px rgba(41,230,154,.10);



&#x20; animation: livePulse 2s infinite;

}





@keyframes livePulse {



&#x20; 50% {

&#x20;   box-shadow:

&#x20;     0 0 0 8px rgba(41,230,154,.03);

&#x20; }



}





.dc-hero h1 {



&#x20; margin: 0;



&#x20; color: #ffffff;



&#x20; font-size: clamp(38px, 5vw, 58px);



&#x20; line-height: 1.08;



&#x20; font-weight: 800;



&#x20; letter-spacing: -2px;

}





.dc-hero h1 span {



&#x20; background:

&#x20;   linear-gradient(

&#x20;     90deg,

&#x20;     #19d7ed,

&#x20;     #67e8f9

&#x20;   );



&#x20; -webkit-background-clip: text;

&#x20; background-clip: text;



&#x20; color: transparent;

}





.hero-description {



&#x20; max-width: 560px;



&#x20; margin: 20px 0 30px;



&#x20; color: #b9cbe3;



&#x20; font-size: 15px;



&#x20; line-height: 1.7;

}





/\* =========================================================

&#x20;  SEARCH

&#x20;  ========================================================= \*/



.dc-search {



&#x20; max-width: 590px;



&#x20; height: 60px;



&#x20; display: flex;

&#x20; align-items: center;



&#x20; position: relative;



&#x20; background: #ffffff;



&#x20; border-radius: 16px;



&#x20; box-shadow:

&#x20;   0 15px 40px rgba(0,0,0,.22);



&#x20; transition:

&#x20;   transform .3s ease,

&#x20;   box-shadow .3s ease;

}





.dc-search:focus-within {



&#x20; transform: translateY(-2px);



&#x20; box-shadow:

&#x20;   0 18px 45px rgba(0,0,0,.28),

&#x20;   0 0 0 3px rgba(24,200,232,.18);

}





.dc-search > i {



&#x20; margin-left: 20px;



&#x20; color: #8da0b8;



&#x20; font-size: 16px;

}





.dc-search input {



&#x20; flex: 1;



&#x20; height: 100%;



&#x20; border: none;



&#x20; outline: none;



&#x20; padding: 0 15px;



&#x20; font-size: 14px;



&#x20; color: #1e293b;



&#x20; background: transparent;

}





.search-action {



&#x20; height: 44px;



&#x20; display: flex;



&#x20; align-items: center;



&#x20; padding: 0 19px;



&#x20; margin-right: 8px;



&#x20; border-radius: 11px;



&#x20; background: #0d5bda;



&#x20; color: #ffffff;



&#x20; font-size: 12px;



&#x20; font-weight: 700;



}





.clear-search {



&#x20; border: none;



&#x20; background: transparent;



&#x20; color: #94a3b8;



&#x20; cursor: pointer;



&#x20; font-size: 13px;

}





/\* =========================================================

&#x20;  HERO TRUST

&#x20;  ========================================================= \*/



.hero-trust {



&#x20; display: flex;



&#x20; gap: 24px;



&#x20; margin-top: 20px;



&#x20; flex-wrap: wrap;

}





.hero-trust span {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 7px;



&#x20; color: #a9c1dd;



&#x20; font-size: 11px;



&#x20; font-weight: 600;

}





.hero-trust i {



&#x20; color: #35dfae;

}





/\* =========================================================

&#x20;  HERO VISUAL

&#x20;  ========================================================= \*/



.dc-hero-visual {



&#x20; width: 380px;

&#x20; height: 380px;



&#x20; position: relative;



&#x20; margin-right: 3%;



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: center;



&#x20; z-index: 3;



&#x20; animation: visualEnter 1s .2s ease both;

}





@keyframes visualEnter {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: scale(.85);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: scale(1);

&#x20; }



}





/\* orbit \*/



.medical-orbit {



&#x20; position: absolute;



&#x20; border: 1px solid rgba(92,220,255,.18);



&#x20; border-radius: 50%;

}





.orbit-one {



&#x20; width: 280px;

&#x20; height: 280px;



&#x20; animation: rotateOrbit 18s linear infinite;

}





.orbit-two {



&#x20; width: 350px;

&#x20; height: 350px;



&#x20; border-style: dashed;



&#x20; animation:

&#x20;   rotateOrbit 25s linear infinite reverse;

}





@keyframes rotateOrbit {



&#x20; to {

&#x20;   transform: rotate(360deg);

&#x20; }



}





/\* center \*/



.medical-core {



&#x20; width: 150px;

&#x20; height: 150px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; position: relative;



&#x20; border-radius: 50%;



&#x20; background:

&#x20;   radial-gradient(

&#x20;     circle at 35% 30%,

&#x20;     #1f8fff,

&#x20;     #06408d 70%

&#x20;   );



&#x20; box-shadow:

&#x20;   0 0 0 18px rgba(18,97,255,.08),

&#x20;   0 0 70px rgba(24,200,232,.25);

}





.core-icon {



&#x20; width: 82px;

&#x20; height: 82px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 50%;



&#x20; background: rgba(255,255,255,.10);



&#x20; border: 1px solid rgba(255,255,255,.18);



&#x20; color: #ffffff;



&#x20; font-size: 34px;



&#x20; z-index: 2;

}





.core-pulse {



&#x20; position: absolute;



&#x20; width: 100%;

&#x20; height: 100%;



&#x20; border-radius: 50%;



&#x20; border: 1px solid rgba(24,200,232,.45);



&#x20; animation: corePulse 2.5s infinite;

}





@keyframes corePulse {



&#x20; 0% {

&#x20;   transform: scale(.9);

&#x20;   opacity: .8;

&#x20; }



&#x20; 100% {

&#x20;   transform: scale(1.5);

&#x20;   opacity: 0;

&#x20; }



}





/\* floating cards \*/



.floating-card {



&#x20; position: absolute;



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 10px;



&#x20; padding: 11px 14px;



&#x20; border-radius: 13px;



&#x20; background: rgba(255,255,255,.10);



&#x20; backdrop-filter: blur(15px);



&#x20; -webkit-backdrop-filter: blur(15px);



&#x20; border: 1px solid rgba(255,255,255,.14);



&#x20; color: #ffffff;



&#x20; box-shadow:

&#x20;   0 12px 35px rgba(0,0,0,.18);



&#x20; animation: floating 4s ease-in-out infinite;

}





.floating-card strong {



&#x20; display: block;



&#x20; font-size: 17px;



&#x20; line-height: 1;

}





.floating-card small {



&#x20; display: block;



&#x20; margin-top: 4px;



&#x20; color: #a8c7e6;



&#x20; font-size: 9px;

}





.floating-icon {



&#x20; width: 34px;

&#x20; height: 34px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 9px;



&#x20; background: rgba(24,200,232,.15);



&#x20; color: #57e4f5;

}





.floating-tests {



&#x20; top: 30px;

&#x20; right: -10px;

}





.floating-results {



&#x20; bottom: 35px;

&#x20; left: -15px;



&#x20; animation-delay: 1s;

}





.floating-secure {



&#x20; bottom: 5px;

&#x20; right: 20px;



&#x20; font-size: 10px;



&#x20; animation-delay: 2s;

}





.floating-secure i {



&#x20; color: #35dfae;

}





@keyframes floating {



&#x20; 0%,100% {

&#x20;   transform: translateY(0);

&#x20; }



&#x20; 50% {

&#x20;   transform: translateY(-9px);

&#x20; }



}





/\* =========================================================

&#x20;  QUICK ACTIONS

&#x20;  ========================================================= \*/



.quick-section {



&#x20; max-width: 1180px;



&#x20; margin: -32px auto 0;



&#x20; padding: 0 25px;



&#x20; position: relative;



&#x20; z-index: 10;



&#x20; display: grid;



&#x20; grid-template-columns: 1fr 1fr;



&#x20; gap: 18px;

}





.quick-card {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 15px;



&#x20; padding: 19px 20px;



&#x20; background: #ffffff;



&#x20; border: 1px solid var(--border);



&#x20; border-radius: 16px;



&#x20; box-shadow:

&#x20;   0 8px 30px rgba(20,50,90,.07);



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   transform .3s ease,

&#x20;   box-shadow .3s ease,

&#x20;   border-color .3s ease;

}





.quick-card:hover {



&#x20; transform: translateY(-5px);



&#x20; border-color: #a9eaf4;



&#x20; box-shadow:

&#x20;   0 15px 35px rgba(20,50,90,.12);

}





.quick-icon {



&#x20; width: 48px;

&#x20; height: 48px;



&#x20; flex-shrink: 0;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 13px;



&#x20; font-size: 19px;

}





.quick-icon.booking {



&#x20; background: #eaf2ff;



&#x20; color: #1261ff;

}





.quick-icon.reports {



&#x20; background: #e9fbf5;



&#x20; color: #0eaf7b;

}





.quick-text {



&#x20; flex: 1;

}





.quick-text span {



&#x20; display: block;



&#x20; color: #8a98aa;



&#x20; font-size: 9px;



&#x20; font-weight: 700;



&#x20; text-transform: uppercase;



&#x20; letter-spacing: 1px;

}





.quick-text strong {



&#x20; display: block;



&#x20; color: #14213d;



&#x20; font-size: 15px;



&#x20; margin: 2px 0;

}





.quick-text small {



&#x20; color: #8997aa;



&#x20; font-size: 11px;

}





.quick-arrow {



&#x20; color: #9ba9b9;



&#x20; transition: transform .25s ease;

}





.quick-card:hover .quick-arrow {



&#x20; transform: translateX(5px);



&#x20; color: #1261ff;

}





/\* =========================================================

&#x20;  CATALOG

&#x20;  ========================================================= \*/



.catalog-section {



&#x20; max-width: 1180px;



&#x20; margin: 65px auto 0;



&#x20; padding: 0 25px;

}





.section-kicker {



&#x20; color: #1477e8;



&#x20; font-size: 10px;



&#x20; font-weight: 800;



&#x20; letter-spacing: 1.5px;

}





.catalog-top h2 {



&#x20; margin: 7px 0 6px;



&#x20; font-size: 28px;



&#x20; color: #14213d;



&#x20; letter-spacing: -.7px;

}





.catalog-top p {



&#x20; margin: 0;



&#x20; color: #7d8b9d;



&#x20; font-size: 13px;

}





/\* =========================================================

&#x20;  CATEGORY

&#x20;  ========================================================= \*/



.category-scroll {



&#x20; display: flex;



&#x20; gap: 9px;



&#x20; overflow-x: auto;



&#x20; padding: 28px 0 6px;



&#x20; scrollbar-width: none;

}





.category-scroll::-webkit-scrollbar {

&#x20; display: none;

}





.category-pill {



&#x20; flex-shrink: 0;



&#x20; padding: 9px 16px;



&#x20; border: 1px solid #e1e8f0;



&#x20; border-radius: 30px;



&#x20; background: #ffffff;



&#x20; color: #637187;



&#x20; font-size: 11px;



&#x20; font-weight: 700;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   all .25s ease;

}





.category-pill i {



&#x20; margin-right: 5px;

}





.category-pill:hover {



&#x20; border-color: #75dcea;



&#x20; color: #0789a8;



&#x20; transform: translateY(-2px);

}





.category-pill.selected {



&#x20; color: #ffffff;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     135deg,

&#x20;     #0b4fd8,

&#x20;     #1298dc

&#x20;   );



&#x20; border-color: transparent;



&#x20; box-shadow:

&#x20;   0 7px 18px rgba(18,97,255,.20);

}





/\* =========================================================

&#x20;  CONTROLS

&#x20;  ========================================================= \*/



.catalog-controls {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: space-between;



&#x20; margin-top: 25px;



&#x20; padding-bottom: 15px;



&#x20; border-bottom: 1px solid #e9eef4;

}





.result-message {



&#x20; color: #8a97a8;



&#x20; font-size: 11px;

}





.result-message strong {



&#x20; color: #14213d;



&#x20; font-size: 13px;

}





.result-message b {



&#x20; color: #1477e8;



&#x20; font-weight: 600;

}





.sort-control {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 7px;



&#x20; color: #8290a2;



&#x20; font-size: 11px;

}





.sort-control i {



&#x20; color: #1477e8;

}





.sort-control select {



&#x20; border: 1px solid #e0e7ef;



&#x20; border-radius: 8px;



&#x20; padding: 7px 10px;



&#x20; background: #ffffff;



&#x20; color: #39475a;



&#x20; outline: none;



&#x20; font-size: 11px;



&#x20; cursor: pointer;

}





/\* =========================================================

&#x20;  GRID

&#x20;  ========================================================= \*/



.diagnostic-grid {



&#x20; display: grid;



&#x20; grid-template-columns:

&#x20;   repeat(

&#x20;     auto-fill,

&#x20;     minmax(285px,1fr)

&#x20;   );



&#x20; gap: 19px;



&#x20; margin-top: 20px;

}





/\* =========================================================

&#x20;  CARD

&#x20;  ========================================================= \*/



.diagnostic-card {



&#x20; background: #ffffff;



&#x20; border: 1px solid #e5ebf2;



&#x20; border-radius: 18px;



&#x20; overflow: hidden;



&#x20; display: flex;



&#x20; flex-direction: column;



&#x20; position: relative;



&#x20; transition:

&#x20;   transform .35s cubic-bezier(.2,.8,.2,1),

&#x20;   box-shadow .35s ease,

&#x20;   border-color .35s ease;



&#x20; animation: cardAppear .55s ease both;

}





@keyframes cardAppear {



&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(18px);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0);

&#x20; }



}





.diagnostic-card:hover {



&#x20; transform: translateY(-7px);



&#x20; border-color: #bcecf4;



&#x20; box-shadow:

&#x20;   0 20px 45px rgba(25,65,105,.11);

}





/\* animated top line \*/



.diagnostic-card::before {



&#x20; content: "";



&#x20; position: absolute;



&#x20; top: 0;

&#x20; left: 0;



&#x20; width: 100%;

&#x20; height: 3px;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     90deg,

&#x20;     #1261ff,

&#x20;     #18c8e8

&#x20;   );



&#x20; transform: scaleX(0);



&#x20; transform-origin: left;



&#x20; transition:

&#x20;   transform .35s ease;

}





.diagnostic-card:hover::before {



&#x20; transform: scaleX(1);

}





/\* =========================================================

&#x20;  CARD TOP

&#x20;  ========================================================= \*/



.diagnostic-top {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: space-between;



&#x20; padding: 20px 20px 5px;

}





.test-symbol {



&#x20; width: 49px;

&#x20; height: 49px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 14px;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     135deg,

&#x20;     #edf7ff,

&#x20;     #e8fbff

&#x20;   );



&#x20; font-size: 25px;



&#x20; transition:

&#x20;   transform .3s ease;

}





.diagnostic-card:hover .test-symbol {



&#x20; transform:

&#x20;   rotate(-4deg)

&#x20;   scale(1.08);

}





.availability {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 5px;



&#x20; padding: 5px 9px;



&#x20; border-radius: 20px;



&#x20; background: #f2faf7;



&#x20; color: #11966b;



&#x20; font-size: 9px;



&#x20; font-weight: 700;

}





.available-dot,

.unavailable-dot {



&#x20; width: 6px;

&#x20; height: 6px;



&#x20; border-radius: 50%;

}





.available-dot {



&#x20; background: #17b77e;



&#x20; box-shadow:

&#x20;   0 0 0 3px rgba(23,183,126,.10);

}





.unavailable-dot {



&#x20; background: #ef5350;

}





/\* =========================================================

&#x20;  CARD BODY

&#x20;  ========================================================= \*/



.diagnostic-body {



&#x20; padding: 17px 20px;



&#x20; flex: 1;

}





.test-category {



&#x20; display: inline-block;



&#x20; margin-bottom: 8px;



&#x20; color: #1477e8;



&#x20; font-size: 9px;



&#x20; font-weight: 800;



&#x20; letter-spacing: .8px;



&#x20; text-transform: uppercase;

}





.diagnostic-body h3 {



&#x20; margin: 0;



&#x20; color: #17253d;



&#x20; font-size: 17px;



&#x20; line-height: 1.3;



&#x20; font-weight: 750;



&#x20; transition:

&#x20;   color .25s ease;

}





.diagnostic-card:hover h3 {



&#x20; color: #086bd5;

}





.test-id {



&#x20; margin-top: 5px;



&#x20; color: #a1adbb;



&#x20; font-family:

&#x20;   "Courier New",

&#x20;   monospace;



&#x20; font-size: 9px;



&#x20; letter-spacing: .3px;

}





.diagnostic-body p {



&#x20; margin: 13px 0 18px;



&#x20; color: #77869a;



&#x20; font-size: 11px;



&#x20; line-height: 1.7;

}





/\* =========================================================

&#x20;  META

&#x20;  ========================================================= \*/



.diagnostic-meta {



&#x20; display: flex;



&#x20; gap: 17px;

}





.diagnostic-meta div {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 6px;



&#x20; color: #748397;



&#x20; font-size: 10px;

}





.diagnostic-meta i {



&#x20; color: #17aaca;



&#x20; font-size: 11px;

}





/\* =========================================================

&#x20;  FOOTER

&#x20;  ========================================================= \*/



.diagnostic-footer {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; justify-content: space-between;



&#x20; padding: 15px 20px;



&#x20; border-top: 1px solid #edf1f5;



&#x20; background: #fbfcfe;

}





.test-price small {



&#x20; display: block;



&#x20; color: #9aa6b5;



&#x20; font-size: 8px;



&#x20; text-transform: uppercase;



&#x20; letter-spacing: .7px;

}





.test-price strong {



&#x20; display: block;



&#x20; margin-top: 2px;



&#x20; color: #122b59;



&#x20; font-size: 21px;



&#x20; font-weight: 800;

}





/\* =========================================================

&#x20;  BOOK BUTTON

&#x20;  ========================================================= \*/



.book-button {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 9px;



&#x20; padding: 10px 14px;



&#x20; border: none;



&#x20; border-radius: 10px;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     135deg,

&#x20;     #1261ff,

&#x20;     #078fd5

&#x20;   );



&#x20; color: #ffffff;



&#x20; font-size: 10px;



&#x20; font-weight: 750;



&#x20; cursor: pointer;



&#x20; box-shadow:

&#x20;   0 6px 15px rgba(18,97,255,.18);



&#x20; transition:

&#x20;   transform .25s ease,

&#x20;   box-shadow .25s ease;

}





.book-button i {



&#x20; transition:

&#x20;   transform .25s ease;

}





.book-button:hover {



&#x20; transform: translateY(-2px);



&#x20; box-shadow:

&#x20;   0 9px 22px rgba(18,97,255,.28);

}





.book-button:hover i {



&#x20; transform: translateX(4px);

}





.book-button.disabled {



&#x20; background: #e8edf3;



&#x20; color: #9aa6b5;



&#x20; box-shadow: none;



&#x20; cursor: not-allowed;

}





/\* =========================================================

&#x20;  EMPTY STATE

&#x20;  ========================================================= \*/



.modern-empty {



&#x20; margin-top: 30px;



&#x20; padding: 75px 25px;



&#x20; text-align: center;



&#x20; background: #ffffff;



&#x20; border: 1px dashed #dce5ef;



&#x20; border-radius: 20px;

}





.empty-circle {



&#x20; width: 65px;

&#x20; height: 65px;



&#x20; margin: 0 auto 18px;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 50%;



&#x20; background: #eef8ff;



&#x20; color: #1477e8;



&#x20; font-size: 22px;

}





.modern-empty h3 {



&#x20; margin: 0 0 7px;



&#x20; color: #1b2a42;



&#x20; font-size: 18px;

}





.modern-empty p {



&#x20; margin: 0 0 20px;



&#x20; color: #8997a8;



&#x20; font-size: 12px;

}





.modern-empty button {



&#x20; padding: 9px 16px;



&#x20; border: none;



&#x20; border-radius: 9px;



&#x20; background: #1261ff;



&#x20; color: #ffffff;



&#x20; font-size: 11px;



&#x20; font-weight: 700;



&#x20; cursor: pointer;



&#x20; transition: transform .2s ease;

}





.modern-empty button:hover {



&#x20; transform: translateY(-2px);

}





/\* =========================================================

&#x20;  BOTTOM NOTE

&#x20;  ========================================================= \*/



.catalog-note {



&#x20; display: flex;



&#x20; align-items: center;



&#x20; gap: 13px;



&#x20; margin-top: 25px;



&#x20; padding: 16px 18px;



&#x20; border-radius: 13px;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     100deg,

&#x20;     #eef8ff,

&#x20;     #f2fdff

&#x20;   );



&#x20; border: 1px solid #d9f0f6;

}





.note-icon {



&#x20; width: 34px;

&#x20; height: 34px;



&#x20; flex-shrink: 0;



&#x20; display: flex;



&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 9px;



&#x20; background: #ffffff;



&#x20; color: #1477e8;



&#x20; font-size: 12px;

}





.catalog-note strong {



&#x20; display: block;



&#x20; color: #23405f;



&#x20; font-size: 11px;

}





.catalog-note span {



&#x20; display: block;



&#x20; margin-top: 3px;



&#x20; color: #8091a5;



&#x20; font-size: 10px;

}





/\* =========================================================

&#x20;  RESPONSIVE

&#x20;  ========================================================= \*/



@media (max-width: 950px) {



&#x20; .dc-hero {



&#x20;   padding: 55px 6%;

&#x20; }



&#x20; .dc-hero-visual {



&#x20;   width: 300px;

&#x20;   height: 300px;



&#x20;   margin-right: 0;

&#x20; }



&#x20; .orbit-one {

&#x20;   width: 230px;

&#x20;   height: 230px;

&#x20; }



&#x20; .orbit-two {

&#x20;   width: 290px;

&#x20;   height: 290px;

&#x20; }



&#x20; .medical-core {

&#x20;   width: 125px;

&#x20;   height: 125px;

&#x20; }



&#x20; .core-icon {

&#x20;   width: 70px;

&#x20;   height: 70px;

&#x20; }



}





@media (max-width: 760px) {



&#x20; .dc-hero {



&#x20;   min-height: auto;



&#x20;   padding: 48px 25px 75px;



&#x20;   flex-direction: column;



&#x20;   align-items: flex-start;

&#x20; }



&#x20; .dc-hero h1 {



&#x20;   font-size: 38px;

&#x20; }



&#x20; .hero-description {



&#x20;   font-size: 13px;

&#x20; }



&#x20; .dc-hero-visual {



&#x20;   display: none;

&#x20; }



&#x20; .quick-section {



&#x20;   grid-template-columns: 1fr;



&#x20;   margin-top: -35px;

&#x20; }



&#x20; .catalog-section {



&#x20;   margin-top: 45px;

&#x20; }



&#x20; .catalog-controls {



&#x20;   align-items: flex-start;



&#x20;   flex-direction: column;



&#x20;   gap: 13px;

&#x20; }



}





@media (max-width: 480px) {



&#x20; .dc-hero {



&#x20;   padding-left: 20px;

&#x20;   padding-right: 20px;



&#x20;   border-radius: 0 0 30px 30px;

&#x20; }



&#x20; .dc-hero h1 {



&#x20;   font-size: 32px;



&#x20;   letter-spacing: -1px;

&#x20; }



&#x20; .dc-search {



&#x20;   height: 54px;

&#x20; }



&#x20; .search-action {



&#x20;   display: none;

&#x20; }



&#x20; .hero-trust {



&#x20;   gap: 12px;

&#x20; }



&#x20; .hero-trust span {



&#x20;   font-size: 10px;

&#x20; }



&#x20; .quick-section {



&#x20;   padding: 0 15px;

&#x20; }



&#x20; .catalog-section {



&#x20;   padding: 0 15px;

&#x20; }



&#x20; .diagnostic-grid {



&#x20;   grid-template-columns: 1fr;

&#x20; }



}

#### **Client controller**



api.controller=function() {

&#x20; var c = this;

&#x20; c.searchQuery = '';

&#x20; c.activeCategory = 'all';

&#x20; c.sortBy = 'name';

&#x20; c.filteredTests = \[];

&#x20; var ICONS = {

&#x20;   'blood': '🩸', 'blood test': '🩸', 'urine': '🧪',

&#x20;   'imaging': '🩻', 'radiology': '🩻', 'cardiology': '❤️',

&#x20;   'neurology': '🧠', 'pathology': '🔬', 'microbiology': '🦠',

&#x20;   'biochemistry': '⚗️', 'genetics': '🧬', 'allergy': '🌿',

&#x20;   'covid': '😷', 'diabetes': '💉', 'thyroid': '🦋',

&#x20;   'liver': '🫁', 'kidney': '🫘', 'vitamin': '💊',

&#x20;   'iron': '🔩', 'ecg': '❤️', 'x-ray': '🩻', 'xray': '🩻'

&#x20; };

&#x20; c.getCategoryIcon = function(category) {

&#x20;   if (!category) return '🔬';

&#x20;   var key = category.toLowerCase();

&#x20;   for (var k in ICONS) {

&#x20;     if (key.indexOf(k) !== -1) return ICONS\[k];

&#x20;   }

&#x20;   return '🔬';

&#x20; };

&#x20; c.truncate = function(text, length) {

&#x20;   if (!text) return 'No description available.';

&#x20;   return text.length > length ? text.substring(0, length) + '...' : text;

&#x20; };

&#x20; c.filterTests = function() {

&#x20;   var all = c.data.tests || \[];

&#x20;   var q = (c.searchQuery || '').toLowerCase().trim();

&#x20;   var cat = c.activeCategory;

&#x20;   c.filteredTests = all.filter(function(t) {

&#x20;     var matchSearch = !q ||

&#x20;       (t.test\_name \&\& t.test\_name.toLowerCase().indexOf(q) !== -1) ||

&#x20;       (t.description \&\& t.description.toLowerCase().indexOf(q) !== -1) ||

&#x20;       (t.test\_code \&\& t.test\_code.toLowerCase().indexOf(q) !== -1) ||

&#x20;       (t.category \&\& t.category.toLowerCase().indexOf(q) !== -1);

&#x20;     var matchCat = (cat === 'all') || (t.category === cat);

&#x20;     return matchSearch \&\& matchCat;

&#x20;   });

&#x20;   c.sortTests();

&#x20; };

&#x20; c.sortTests = function() {

&#x20;   var t = c.filteredTests;

&#x20;   if (c.sortBy === 'name') {

&#x20;     t.sort(function(a, b) { return (a.test\_name || '').localeCompare(b.test\_name || ''); });

&#x20;   } else if (c.sortBy === 'price\_asc') {

&#x20;     t.sort(function(a, b) { return (a.price || 0) - (b.price || 0); });

&#x20;   } else if (c.sortBy === 'price\_desc') {

&#x20;     t.sort(function(a, b) { return (b.price || 0) - (a.price || 0); });

&#x20;   } else if (c.sortBy === 'duration') {

&#x20;     t.sort(function(a, b) { return (a.test\_duration || '').localeCompare(b.test\_duration || ''); });

&#x20;   }

&#x20; };

&#x20; c.setCategory = function(cat) {

&#x20;   c.activeCategory = cat;

&#x20;   c.filterTests();

&#x20; };

&#x20; c.clearSearch = function() {

&#x20;   c.searchQuery = '';

&#x20;   c.filterTests();

&#x20; };

&#x20; c.resetFilters = function() {

&#x20;   c.searchQuery = '';

&#x20;   c.activeCategory = 'all';

&#x20;   c.sortBy = 'name';

&#x20;   c.filterTests();

&#x20; };

&#x20; var \_getPortal = function() {

&#x20;   return window.location.pathname.split('/')\[1] || 'sp';

&#x20; };

&#x20; c.bookTest = function(test) {

&#x20;   sessionStorage.setItem('selected\_test\_sys\_id', test.sys\_id);

&#x20;   sessionStorage.setItem('selected\_test\_name', test.test\_name || '');

&#x20;   sessionStorage.setItem('selected\_test\_price', test.price || 0);

&#x20;   sessionStorage.setItem('selected\_test\_code', test.test\_code || '');

&#x20;   sessionStorage.setItem('selected\_test\_category', test.category || '');

&#x20;   sessionStorage.setItem('selected\_test\_duration', test.test\_duration || '');

&#x20;   window.location.href = '/' + \_getPortal() + '?id=appointment\_booking';

&#x20; };

&#x20; c.goToMyBookings = function() {

&#x20;   window.location.href = '/' + \_getPortal() + '?id=my\_appointments';

&#x20; };

&#x20; c.goToMyReports = function() {

&#x20;   window.location.href = '/' + \_getPortal() + '?id=lab\_reports';

&#x20; };

&#x20; // INIT

&#x20; c.filteredTests = angular.copy(c.data.tests || \[]);

&#x20; c.data.totalTests = c.filteredTests.length;

&#x20; c.sortTests();

}

#### 

#### **Server script**



(function() {

&#x20; data.tests = \[];

&#x20; data.categories = \[];

&#x20; data.totalTests = 0;

&#x20; try {

&#x20;   var testGr = new GlideRecord('x\_1989050\_medica\_0\_diagnostic\_test');

&#x20;   testGr.orderBy('test\_name');

&#x20;   testGr.query();

&#x20;   var categorySet = {};

&#x20;   var categoryList = \[];

&#x20;   while (testGr.next()) {

&#x20;     var categoryDisplay = testGr.getDisplayValue('category') || testGr.getValue('category') || 'General';

&#x20;     var activeVal = testGr.getValue('active');

&#x20;     var isActive = (activeVal === '1' || activeVal === 'true' || activeVal === true);

&#x20;     data.tests.push({

&#x20;       sys\_id:        testGr.getUniqueValue(),

&#x20;       test\_name:     testGr.getValue('test\_name')     || '',

&#x20;       test\_code:     testGr.getValue('test\_code')     || '',

&#x20;       category:      categoryDisplay,

&#x20;       description:   testGr.getValue('description')   || '',

&#x20;       price:         parseFloat(testGr.getValue('price')) || 0,

&#x20;       test\_duration: testGr.getValue('test\_duration') || '',

&#x20;       active:        isActive

&#x20;     });

&#x20;     if (categoryDisplay \&\& !categorySet\[categoryDisplay]) {

&#x20;       categorySet\[categoryDisplay] = true;

&#x20;       categoryList.push(categoryDisplay);

&#x20;     }

&#x20;   }

&#x20;   categoryList.sort();

&#x20;   data.categories = categoryList;

&#x20;   data.totalTests = data.tests.length;

&#x20; } catch(e) {

&#x20;   data.error = e.message;

&#x20;   gs.error('MediCare Catalog Error: ' + e.message);

&#x20; }

})();

