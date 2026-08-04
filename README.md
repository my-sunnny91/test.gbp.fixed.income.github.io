import { useState } from "react";
import { ShieldCheck, TrendingUp, Users, Wallet } from "lucide-react";
import DashboardHeader from "@/components/dashboard/DashboardHeader";
import MetricCard from "@/components/dashboard/MetricCard";
import PerformanceChart from "@/components/dashboard/PerformanceChart";
import AllocationCard from "@/components/dashboard/AllocationCard";
import HoldingsTable from "@/components/dashboard/HoldingsTable";
import FlowsCard from "@/components/dashboard/FlowsCard";
import CommentarySection from "@/components/dashboard/CommentarySection";
import { allocation, fundMonths, holdings } from "@/lib/fundData";

export default function Home() {
  const [month, setMonth] = useState("July 2026");
  const data = fundMonths[month];
  const metrics = [
    ["Net asset value", data.nav, data.changes[0], Wallet],
    ["Monthly return", data.return, data.changes[1], TrendingUp],
    ["Annualized volatility", data.volatility, data.changes[2], ShieldCheck, true],
    ["Active investors", data.investors, data.changes[3], Users]
  ];
  return (
    <main className="min-h-screen bg-background">
      <div className="mx-auto max-w-7xl px-4 py-8 sm:px-6 lg:px-8 lg:py-12">
        <DashboardHeader month={month} setMonth={setMonth} months={Object.keys(fundMonths)} asOf={data.asOf} />
        <CommentarySection month={month} asOf={data.asOf} />
        <div className="mt-8 grid gap-4 sm:grid-cols-2 lg:grid-cols-4">{metrics.map(([label,value,change,icon,inverse]) => <MetricCard key={label} label={label} value={value} change={change} icon={icon} inverse={inverse} />)}</div>
        <div className="mt-6 grid gap-6 lg:grid-cols-3"><PerformanceChart data={data.performance} /><AllocationCard data={allocation} /></div>
        <div className="mt-6 grid gap-6 lg:grid-cols-3"><HoldingsTable holdings={holdings} /><FlowsCard data={data.flows} /></div>
        <p className="mt-8 text-center text-xs text-muted-foreground">Performance shown net of management fees. Past performance is not indicative of future results.</p>
      </div>
    </main>
  );
}
