# starbucks-clone-website
## 개요 : 프론트엔드 웹 개발의 모든 것 초격차 패키지 Online.강의를 보며 css 학습한 결과물입니다.
## REACT
- [REACT](https://github.com/JunBum2ya/starbuks-clone-website-react)
## 배포
   - [netlify](https://rad-platypus-bf3217.netlify.app/)
## 기술 스택
- 바닐라 자바스크립트로 html과 css에 중점을 두었습니다.
1. html
2. css
3. javascript
   - swiper : 스와이퍼 기능 구현
   - loadash : 스크롤 이벤트 제어
   - gsap : 애니메이션 구현
   - youtube.js : youtube 컨텐츠 추가
   - scrollMagic.js : 스크롤 감시
## 구성
   1. swiper 
      ```javascript
      // 진행중인 공지사항 swiper
      new Swiper('.notice-line .swiper-container', {
         direction: 'vertical',
         autoplay: true,
         loop: true
      });
      // 프로모션 swiper
      new Swiper('.promotion .swiper-container', {
         slidesPerView: 3,
         spaceBetween: 10,
         centeredSlides: true,
         loop: true,
         autoplay: {
            delay: 5000
         },
         pagination: {
            el: '.promotion .swiper-pagination',
            clickable: true
         },
         navigation: {
            prevEl: '.promotion .swiper-prev',
            nextEl: '.promotion .swiper-next'
         }
      });
      ```
   1. 애니메이션
   ```javascript
      //스크롤을 500px까지 내리면 이벤트 발생(loadash.js로 이벤트 제어)
      const badgesEl = document.querySelector("header .badges");
      window.addEventListener('scroll',_.throttle((ev) => {
      if(window.scrollY > 500) {
         gsap.to(badgesEl, .6, {
            opacity : 0,
            display: 'none'
         });
         gsap.to('#to-top', .2, {
            x: 0
         });
      } else {
         gsap.to(badgesEl, .6, {
            opacity : 1,
            display: 'block'
         });
         gsap.to('#to-top', .2, {
            x: 100
         });
      }
      }, 300));

      //최상단 이동 버튼을 클릭 시 웹페이지의 최상단으로 이동
      const toTopEl = document.querySelector('#to-top');
      toTopEl.addEventListener('click',() => {
         gsap.to(window, .7, {
            scrollTo: 0
         });
      });
   ```
   1. 스크롤 트리거
   ```javascript
   //스크롤 이벤트를 감시하여 일정 스크롤 위치에 도달하면 show 클래스 추가
   const spyEls = document.querySelectorAll('section.scroll-spy');
   spyEls.forEach((spyEl,index) => {
      new ScrollMagic
      .Scene({
         triggerElement: spyEl,
         triggerHook: .8
      })
      .setClassToggle(spyEl, 'show')
      .addTo(new ScrollMagic.Controller());
   });
   ```
