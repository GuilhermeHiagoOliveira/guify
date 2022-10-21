<template>
  <div class="sidebar bg-black p-4">
    <div>
      <div class="logo mb-4">
          <img src="img/guify-logo.png" alt="" id="guify-logo" />
      </div>

      <div class="d-flex flex-row align-items-center mb-3">
        <div class="me-3">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="28"
            width="28"
            viewBox="0 0 48 48"
          >
            <path d="M8 42V18L24.1 6 40 18v24H28.3V27.75h-8.65V42Z" />
          </svg>
        </div>
        <div>
          <label class="menu-label active">Início</label>
        </div>
      </div>

      <div class="d-flex flex-row align-items-center mb-3">
        <div class="me-3">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="28"
            width="28"
            viewBox="0 0 48 48"
          >
            <path
              d="M39.8 41.95 26.65 28.8q-1.5 1.3-3.5 2.025-2 .725-4.25.725-5.4 0-9.15-3.75T6 18.75q0-5.3 3.75-9.05 3.75-3.75 9.1-3.75 5.3 0 9.025 3.75 3.725 3.75 3.725 9.05 0 2.15-.7 4.15-.7 2-2.1 3.75L42 39.75Zm-20.95-13.4q4.05 0 6.9-2.875Q28.6 22.8 28.6 18.75t-2.85-6.925Q22.9 8.95 18.85 8.95q-4.1 0-6.975 2.875T9 18.75q0 4.05 2.875 6.925t6.975 2.875Z"
            />
          </svg>
        </div>
        <div>
          <label class="menu-label">Buscar</label>
        </div>
      </div>

      <div class="d-flex flex-row align-items-center mb-5">
        <div class="me-3">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="28"
            width="28"
            viewBox="0 0 48 48"
          >
            <path
              d="M24.3 31.35q2.05 0 3.5-1.425 1.45-1.425 1.45-3.475v-12.6h5.8v-3h-7.8V22.7q-.55-.45-1.325-.7-.775-.25-1.625-.25-1.95 0-3.3 1.375-1.35 1.375-1.35 3.325 0 2 1.35 3.45 1.35 1.45 3.3 1.45ZM13 38q-1.2 0-2.1-.9-.9-.9-.9-2.1V7q0-1.2.9-2.1.9-.9 2.1-.9h28q1.2 0 2.1.9.9.9.9 2.1v28q0 1.2-.9 2.1-.9.9-2.1.9Zm-6 6q-1.2 0-2.1-.9Q4 42.2 4 41V10h3v31h31v3Z"
            />
          </svg>
        </div>
        <div>
          <label class="menu-label">Sua Biblioteca</label>
        </div>
      </div>

      <div class="d-flex flex-row align-items-center mb-3">
        <div class="me-3">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="30"
            width="30"
            viewBox="0 0 48 48"
          >
            <path
              d="M22.5 34h3v-8.5H34v-3h-8.5V14h-3v8.5H14v3h8.5ZM9 42q-1.2 0-2.1-.9Q6 40.2 6 39V9q0-1.2.9-2.1Q7.8 6 9 6h30q1.2 0 2.1.9.9.9.9 2.1v30q0 1.2-.9 2.1-.9.9-2.1.9Z"
            />
          </svg>
        </div>
        <div>
          <label class="menu-label">Criar playlist</label>
        </div>
      </div>

      <div class="d-flex flex-row align-items-center mb-3">
        <div class="me-3">
          <div class="likeSongs">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              height="14"
              width="14"
              viewBox="0 0 48 48"
            >
              <path
                d="m24 41.95-2.05-1.85q-5.3-4.85-8.75-8.375-3.45-3.525-5.5-6.3T4.825 20.4Q4 18.15 4 15.85q0-4.5 3.025-7.525Q10.05 5.3 14.5 5.3q2.85 0 5.275 1.35Q22.2 8 24 10.55q2.1-2.7 4.45-3.975T33.5 5.3q4.45 0 7.475 3.025Q44 11.35 44 15.85q0 2.3-.825 4.55T40.3 25.425q-2.05 2.775-5.5 6.3T26.05 40.1Z"
              />
            </svg>
          </div>
        </div>
        <div>
          <label class="menu-label">Músicas curtidas</label>
        </div>
      </div>

      <hr />
    </div>
  </div>
</template>
