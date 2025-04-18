# My-Profile
import React, { useEffect, useRef } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { motion } from "framer-motion";

const socialLinks = [
  { name: "Instagram", url: "https://instagram.com/lxstshin" },
  { name: "github", url: "https://github.com/kshitij-tech297" },
  { name: "Discod", url: "https://discord.gg/zimt17" },
  
];

const pictures = [
  "/images/pic1.jpg",
  "/images/pic2.jpg",
  "/images/pic3.jpg",
];

export default function SocialMediaPortfolio() {
  const audioRef = useRef(null);

  useEffect(() => {
    const audio = audioRef.current;
    if (audio) {
      audio.volume = 0.5;
      audio.play().catch(e => console.log("Autoplay blocked or error:", e));
    }
  }, []);

  return (
    <div className="p-8 max-w-5xl mx-auto grid gap-6">
      <audio ref={audioRef} loop autoPlay hidden>
        <source src="/music/favorite-song.mp3" type="audio/mpeg" />
        Your browser does not support the audio element.
      </audio>

      <motion.h1
        className="text-4xl font-bold text-center"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.5 }}
      >
        My Social Media Portfolio
      </motion.h1>

      <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
        {socialLinks.map((link, idx) => (
          <motion.a
            key={idx}
            href={link.url}
            target="_blank"
            rel="noopener noreferrer"
            whileHover={{ scale: 1.1 }}
            className="block"
          >
            <Card className="rounded-2xl shadow-lg">
              <CardContent className="p-4 text-center">
                <p className="text-lg font-medium">{link.name}</p>
              </CardContent>
            </Card>
          </motion.a>
        ))}
      </div>

      <div className="grid grid-cols-1 sm:grid-cols-3 gap-4">
        {pictures.map((src, idx) => (
          <motion.img
            key={idx}
            src={src}
            alt={`Picture ${idx + 1}`}
            className="w-full h-64 object-cover rounded-2xl shadow-md"
            whileHover={{ scale: 1.05 }}
          />
        ))}
      </div>

      <motion.div
        className="mt-10"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ delay: 0.5 }}
      >
        <h2 className="text-2xl font-semibold text-center mb-4">3D Brawl Stars Animation</h2>
        <div className="w-full h-[500px] bg-gray-100 rounded-2xl flex items-center justify-center shadow-inner">
          {/* Embed or render your Brawl Stars 3D animation here */}
          <p className="text-gray-500">[3D animation placeholder]</p>
        </div>
      </motion.div>
    </div>
  );
}
