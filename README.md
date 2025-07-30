// frontend/pages/index.js
import { useRouter } from 'next/router';
import { useState } from 'react';

export default function Home() {
  const [specialty, setSpecialty] = useState('');
  const [location, setLocation] = useState('');
  const router = useRouter();

  const handleSearch = (e) => {
    e.preventDefault();
    router.push(`/search?specialty=${specialty}&location=${location}`);
  };

  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-100 p-4">
      <form onSubmit={handleSearch} className="bg-white p-6 rounded-lg shadow-md w-full max-w-xl space-y-4">
        <input type="text" placeholder="Specialty" value={specialty} onChange={(e) => setSpecialty(e.target.value)} className="w-full p-2 border rounded" required />
        <input type="text" placeholder="Location" value={location} onChange={(e) => setLocation(e.target.value)} className="w-full p-2 border rounded" required />
        <button type="submit" className="w-full bg-blue-500 text-white p-2 rounded">Search Doctors</button>
      </form>
    </div>
  );
}
