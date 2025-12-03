chagpt desktop (raccourcis rapide et mini fenètre)

utiliser l'ia pour des questions, auto completion, 

![[Pasted image 20250915094916.png]]


#import { defineConfig } from 'vite';
#import react from '@vitejs/plugin-react';
#
#export default defineConfig({
#  base: process.env.NODE_ENV === 'production' ? '/2048-game/' : './',
#  server: {
#    port: 3000,
#   host: '0.0.0.0',
#  },
#  plugins: [react()],
#  build: {
#    outDir: 'dist',
#    sourcemap: true,
#    rollupOptions: {
#      output: {
#        manualChunks: {
#          vendor: ['react', 'react-dom'],
#        },
#      },
#    },
#  },
#  optimizeDeps: {
#    include: ['react', 'react-dom'],
#  },
#});
