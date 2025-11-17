/**
 * chr291 - Player Portfolio (single-file React component)
 * -----------------------------------------------------
 * Instructions:
 * 1) Upload the images you want to include and name them exactly as below (or edit paths):
 *    - /images/CHR.jpg        (recommended 600x600)
 *    - /images/chr coke.jpg         (recommended 1280x720)
 *    - /images/Chrs gamerværelse.jpg         (recommended 1280x720)
 *    - /images/CHR.jpg         (recommended 1280x720)
 *    - /images/achievement-badge.png (optional small icon)
 *
 * 2) If you want to include video clips, paste YouTube or Twitch clip URLs in the `clips` array below.
 * 3) Copy this file into a React app (Vite/Next/CRA). Tailwind is used for styling (no import required here).
 * 4) Customize the stats, quotes, and colors in the `PROFILE` object.
 *
 * If you prefer, upload images in the chat and tell me the filenames; I can replace placeholders for you.
 */

import React from 'react';

// ---------- EDIT THIS PROFILE DATA ----------
const PROFILE = {
  name: 'chr291',
  tagline: 'Aim. Clutch. Dominate.',
  about:
    'Competitive sharpshooter — crisp aim, immaculate utility usage, and clutch instincts. Consistently carries matches and turns mid-round chaos into highlight reels.',
  stats: [
    { label: 'ADR (avg damage round)', value: '132' },
    { label: 'K/D', value: '2.4' },
    { label: 'Clutch %', value: '18%' },
    { label: 'Headshot %', value: '46%' },
  ],
  clips: [
    // add public URLs to highlight videos (YouTube/Twitch)
    // 'https://www.youtube.com/watch?v=EXAMPLE1',
    // 'https://www.youtube.com/watch?v=EXAMPLE2',
  ],
};

// ---------- COMPONENT ----------
export default function Chr291Portfolio() {
  return (
    <main className="min-h-screen bg-gradient-to-b from-gray-900 to-gray-800 text-white p-6">
      <div className="max-w-6xl mx-auto">
        {/* Header */}
        <header className="flex flex-col md:flex-row items-center gap-6 md:gap-12">
          <div className="w-40 h-40 rounded-2xl overflow-hidden ring-2 ring-white/10">
            <img
              src="/images/headshot.jpg"
              alt="chr291 headshot"
              className="w-full h-full object-cover"
              onError={(e) => (e.currentTarget.style.display = 'none')}
            />
          </div>

          <div className="flex-1">
            <h1 className="text-4xl md:text-5xl font-extrabold tracking-tight">{PROFILE.name}</h1>
            <p className="mt-2 text-lg text-gray-200">{PROFILE.tagline}</p>

            <p className="mt-4 max-w-2xl text-gray-300">{PROFILE.about}</p>

            <div className="mt-6 flex flex-wrap gap-3">
              <a
                href="#play"
                className="inline-block px-5 py-2 rounded-lg bg-white/8 backdrop-blur-sm hover:bg-white/12 text-sm"
              >
                Join a pickup
              </a>
              <a
                href="#clips"
                className="inline-block px-5 py-2 rounded-lg border border-white/8 hover:bg-white/6 text-sm"
              >
                Watch highlights
              </a>
            </div>
          </div>

          {/* Achievement Badge (small) */}
          <div className="hidden md:block">
            <img
              src="/images/achievement-badge.png"
              alt="achievement badge"
              className="w-28 h-28 object-contain"
              onError={(e) => (e.currentTarget.style.display = 'none')}
            />
          </div>
        </header>

        {/* Stats */}
        <section className="mt-10 grid grid-cols-2 md:grid-cols-4 gap-4">
          {PROFILE.stats.map((s) => (
            <div
              key={s.label}
              className="p-4 rounded-xl bg-white/5 border border-white/6 text-center"
            >
              <div className="text-2xl font-bold">{s.value}</div>
              <div className="mt-1 text-sm text-gray-300">{s.label}</div>
            </div>
          ))}
        </section>

        {/* Gallery */}
        <section id="gallery" className="mt-12">
          <h2 className="text-2xl font-semibold">Match Highlights</h2>
          <p className="mt-2 text-gray-300">A few recent clutches and jaw-dropping rounds.</p>

          <div className="mt-6 grid grid-cols-1 md:grid-cols-3 gap-4">
            <GalleryItem src="/images/action1.jpg" alt="action 1" caption="Triple entry + AWP clutch" />
            <GalleryItem src="/images/action2.jpg" alt="action 2" caption="4k retake with nade lineup" />
            <GalleryItem src="/images/action3.jpg" alt="action 3" caption="1v3 pistol ace" />
          </div>
        </section>

        {/* Clips */}
        <section id="clips" className="mt-12">
          <h2 className="text-2xl font-semibold">Video Highlights</h2>
          <p className="mt-2 text-gray-300">Click to open in a new tab.</p>

          <div className="mt-4 flex flex-col gap-4">
            {PROFILE.clips.length === 0 ? (
              <div className="text-gray-400">No clips added yet — add YouTube/Twitch links in the profile data.</div>
            ) : (
              PROFILE.clips.map((url, i) => (
                <a
                  key={i}
                  href={url}
                  target="_blank"
                  rel="noopener noreferrer"
                  className="p-4 rounded-lg border border-white/6 bg-white/3"
                >
                  {url}
                </a>
              ))
            )}
          </div>
        </section>

        {/* Footer / Call to Action */}
        <footer id="play" className="mt-16 p-6 rounded-xl bg-white/3 border border-white/6 flex flex-col md:flex-row items-center justify-between gap-4">
          <div>
            <h3 className="text-xl font-semibold">Want to queue with {PROFILE.name}?</h3>
            <p className="mt-1 text-gray-200">Join the Steam group, drop a message, and get a chance to play with a top-tier player.</p>
          </div>

          <div className="flex gap-3">
            <a href="#" className="px-4 py-2 rounded-lg bg-green-600 hover:bg-green-700">Steam Group</a>
            <a href="#" className="px-4 py-2 rounded-lg border border-white/6">Discord</a>
          </div>
        </footer>

        <p className="mt-6 text-xs text-gray-500">Built with ❤️ — edit the file to customize copy, images and stats.</p>
      </div>
    </main>
  );
}

function GalleryItem({ src, alt, caption }) {
  return (
    <figure className="rounded-xl overflow-hidden bg-white/4 border border-white/6">
      <img src={src} alt={alt} className="w-full h-56 object-cover" onError={(e) => (e.currentTarget.style.display = 'none')} />
      <figcaption className="p-3 text-sm text-gray-300">{caption}</figcaption>
    </figure>
  );
}
